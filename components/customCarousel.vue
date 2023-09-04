<template>
    <v-col
        class="custom-carousel"
        cols="12"
        justify="center" align="center"
    >
        <v-carousel
        :cycle="false"
        :continuous="false"
        :hide-delimiters="true"
        show-arrows-on-hover 
        draggable="true"
        height="auto"
        >
            <v-carousel-item
                v-for="(pair, index) in testimonialsPairs"
                :key="index"
            >
                <v-row>
                    <v-col v-for="testimonial in pair" :key="testimonial.id">
                        <v-card class="custom-carousel__card" align="left">
                            <v-card-text class="custom-carousel__text"><q>{{ testimonial.body }}</q></v-card-text>
                            <div class="custom-carousel__profile">
                                <img class="custom-carousel__img" src="../static/images/avatar-1.png">
                                <v-card-text class="custom-carousel__userid">{{ testimonial.id }} <br> <p class="custom-carousel__userid-title">{{ testimonial.title }}</p></v-card-text>
                            </div>
                        </v-card>
                    </v-col>
                </v-row>
            </v-carousel-item>
        </v-carousel>
    </v-col>
</template>

<script>
export default {
    props: {
        testimonials: Array,
    },
    data() {
        return {
        
        };
    },
    computed: {
        testimonialsPairs() {
        const pairs = [];
        for (let i = 0; i < this.testimonials.length; i += 2) {
            pairs.push(this.testimonials.slice(i, i + 2));
        }
        return pairs;
        },
    }
};
</script>
  
<style lang="scss">
q::before {
    color: #303644;
}

q::after {
    color: #303644;
}

.custom-carousel {
    padding-bottom: 50px !important;

    &__card {
        background-color: #ffffff !important;
        border-radius: 30px !important;
        min-height: 400px;
        max-width: 650px;
        min-width: 290px;
        padding: 40px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        overflow:visible;
    }

    &__text {
        color: #6D6D6D !important;
        font-family: 'cfastystd-light-webfont', sans-serif;
        font-size: 24px;
        font-weight: 700;
        padding: 0;
        line-height: 1.5;
    }

    &__profile {
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    &__userid {
        color: #000000 !important;
        font-family: 'cfastystd-bold-webfont', sans-serif;
        font-size: 24px;

        &-title {
            margin: 0 !important;
            color: #6D6D6D !important;
            font-family: 'cfastystd-light-webfont', sans-serif;
            font-size: 18px;
        }
    }
}
</style>