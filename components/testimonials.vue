<template>
    <v-row justify="center" align="center" class="ma-0">
      <v-col class="testimonials" :class="$vuetify.breakpoint.lgAndUp ? 'py-16' : ''" justify="center" align="center" cols="12">
        <h1 class="testimonials-title">Testimonials</h1>
        <p class="testimonials-subinfo">Need even more convincing? <br> Here is what our customers say about us</p>
      </v-col>
      <CustomCarousel class="testimonials" :testimonials="testimonials" />
      <v-col class="testimonials brands" :class="$vuetify.breakpoint.lgAndUp ? 'py-16' : ''" justify="center" align="center" cols="12">
        <v-img class="img" :width="$vuetify.breakpoint.lgAndUp ? '90' : '120'" :height="$vuetify.breakpoint.lgAndUp ? '90' : '60'" v-for="img of brandImgs" :src="require(`~/static/images/${img.img}`)"></v-img>
      </v-col>
    </v-row>
</template>

<style lang="scss">
.testimonials {
    background-color: #FAD069;

    &-title {
        color: #303644;
        font-family: 'cfastystd-bold-webfont', sans-serif;
        font-size: 48px;
    }

    &-subinfo {
        color: #303644;
        font-family: 'cfastystd-light-webfont', sans-serif;
        font-size: 24px;
        font-weight: 700;
    }
}

.brands {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;

  .img {
    filter: sepia(100%) hue-rotate(10deg);
  }
}

@media only screen and (max-width: 1260px) {
  .brands {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}
</style>
  
<script>
import customCarousel from "@/components/customCarousel.vue";

export default {
    components: {
        customCarousel,
    },
    name: 'Testimonials',
    data() {
      return {
        testimonials: [],
        brandImgs: [
          {
            img: 'logo-1.svg'
          },{
            img: 'logo-2.svg'
          },{
            img: 'logo-3.svg'
          },{
            img: 'logo-4.svg'
          },{
            img: 'logo-5.svg'
          },{
            img: 'logo-6.svg'
          },{
            img: 'logo-7.svg'
          },{
            img: 'logo-8.svg'
          },
        ]
      }
    },
    computed: {
        testimonialsPairs() {
            const pairs = [];
            for (let i = 0; i < this.testimonials.length; i += 2) {
                pairs.push(this.testimonials.slice(i, i + 2));
            }
            return pairs;
        },
    },
    methods: {
      async getTestimonials() {
            try {
                const response = await this.$axios.get('https://jsonplaceholder.typicode.com/posts');
                this.testimonials = response.data;
                console.log(this.testimonials)
            } catch (error) {
                console.error('Error fetching posts:', error);
            }
        }
    },
    beforeMount() {
      this.getTestimonials();
    },
  }
</script>  