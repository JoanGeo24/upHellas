<template>
  <v-row justify="center" align="center">
    <v-col :class="$vuetify.breakpoint.lgAndUp ? 'py-16' : ''" justify="center" align="center" cols="12">
      <header>
        <img class="logo" src="../static/images/uphellas-logo.svg">
      </header>
    </v-col>
    <div class="section">
      <v-col :class="$vuetify.breakpoint.lgAndUp ? 'pl-16' : ''" class="py-0 mt-6 section--left" justify="center" align="left" cols="12" sm="12" md="6">
        <img class="badge mt-4" src="../static/images/5-badge.svg">
        <h1 class="section__title">Here's a <br> crazy thought</h1>
        <p class="section__paragraph">Happy & healthy employees work better!</p>
        <button class="section__btn" @click="scrollToCardsSection">Find out how we can help</button>
      </v-col>
      <v-col :class="$vuetify.breakpoint.lgAndUp ? 'pr-16' : ''" class="py-0 pl-0" justify="center" align="center" cols="12" sm="12" md="6">
          <img class="section__img" src="../static/images/banner-image.png">
      </v-col>
    </div>
    <v-col :class="$vuetify.breakpoint.lgAndUp ? 'px-16' : ''" class="py-0" justify="center" align="center" cols="12" sm="12" md="6">
      <p class="ma-0 section__scroll">Scroll for more</p>
      <v-icon class="section__scroll-icon">mdi-chevron-down</v-icon>
    </v-col>
    <v-col :class="$vuetify.breakpoint.lgAndUp ? 'px-16' : ''" class="py-0 mt-16" justify="center" align="center" cols="12">
      <p class="section__second-title px-6">Happy & healthy employees work better! &#128153;</p>
      <p class="section__second-subinfo px-6">We are Up. We design and deliver digital-first employee benefits that transform the workplace experience.</p>
    </v-col>
    <v-col :class="$vuetify.breakpoint.lgAndUp ? 'px-16' : ''" class="py-0 my-16 section__second-cards" justify="center" align="center" cols="12" ref="cardsSection">
      <v-card
        v-for="(card, index) in cardImages"
        :key="index"
        :class="{'mx-3 my-12 card': true, 'hovered-card': card.isHovered}"        width="320"
        height="510"
        @mouseover="isHovered(index)"
        @mouseout="isNotHovered(index)"
      >
        <div class="card__content">
          <v-img
            max-width="250"
            :src="card.titleImg"
            class="card__title-image"
          ></v-img>

          <v-card-text class="card__title-text">{{ card.title }}</v-card-text>

          <v-img
            height="250"
            :src="card.img"
            class="card__image"
          ></v-img>

          <v-card-actions>
            <v-btn
              text
              @click="scrollToTellMeMoreSection"
              class="card__button"
              :class="{ 'show-button': card.isHovered }"
            >
              Learn More
            </v-btn>
          </v-card-actions>
        </div>
      </v-card>
    </v-col>
    <div class="section section__third section__benefits">
      <v-col :class="$vuetify.breakpoint.lgAndUp ? 'pl-16' : ''" class="section--left" justify="center" align="center" cols="12" sm="12" md="6">
        <h1 class="section__title">The unrivalled meal <br> card solution</h1>
        <v-card
          class="section__benefits-card"
          max-width="650"
          min-width="300"
        >
        <div :class="$vuetify.breakpoint.lgAndUp ? 'ml-7' : 'ml-2'" class="my-3 mr-2">
          <div class="section__benefits-card-title">
            <img
              max-width="250"
              src="../static/images/go-for-eat.svg"
              :class="$vuetify.breakpoint.mdAndDown ? 'mb-3' : ''"
            >
            <p class="chip" :class="$vuetify.breakpoint.mdAndDown ? 'mb-3' : ''"
>Meal card</p>
            <img
              height="100"
              src="../static/images/card.png"
            >
          </div>

          <v-card-text class="section__benefits-title">Enjoy your meals anywhere you want</v-card-text>

          <v-card-text class="section__benefits-text">Our prepaid meal card by Mastercard is designed to offer to both our corporate customers and users an unmatched experience that's simple & fun.</v-card-text>

          <v-card-text class="section__benefits-text--tip">Tax exemption: 6 euros per day / 1,452 euros per year per employee</v-card-text>

          <div class="section__benefits-text--list">
            <p class="title">Benefits</p>
            <p class="list--item"><v-icon class="icon">mdi-check-bold</v-icon> Order & load cards online in seconds, download invoices & reports in a click</p>
            <p class="list--item"><v-icon class="icon">mdi-check-bold</v-icon> Best in class service: Quantified & qualified with a monthly report</p>
            <p class="list--item"><v-icon class="icon">mdi-check-bold</v-icon> Our cards are accepted everywhere in Greece</p>
            <p class="list--item"><v-icon class="icon">mdi-check-bold</v-icon> Use our app for full control & mobile payments</p>
          </div>
        </div>

          <v-card-actions class="section__third-action section__benefits-action">
            <button
              @click="scrollToTellMeMoreSection"
              class="section__third-btn section__benefits-btn"
            >
              Contact us 
              <v-icon class="icon">mdi-arrow-right-bold-outline</v-icon>
            </button>
          </v-card-actions>
        </v-card>
      </v-col>
      <v-col :class="$vuetify.breakpoint.lgAndUp ? 'pr-16' : ''" justify="center" align="center" cols="12" sm="12" md="6">
        <img class="section__img" src="../static/images/goforeat.png">
      </v-col>
    </div>
    <div class="section section__fourth section__benefits">
      <v-col :class="$vuetify.breakpoint.lgAndUp ? 'pr-16' : ''" justify="center" align="center" cols="12" sm="12" md="6">
        <img class="section__img" src="../static/images/upgift.png">
      </v-col>
      <v-col :class="$vuetify.breakpoint.lgAndUp ? 'pl-16' : ''" class="section--left" justify="center" align="center" cols="12" sm="12" md="6">
        <h1 class="section__title">The perfect gift</h1>
        <v-card
          class="section__benefits-card"
          max-width="650"
          min-width="300"
        >
        <div :class="$vuetify.breakpoint.lgAndUp ? 'ml-7' : 'ml-2'" class="my-3 mr-2">
          <div class="section__benefits-card-title">
            <img
              max-width="250"
              src="../static/images/UP-GIFT.svg"
              :class="$vuetify.breakpoint.mdAndDown ? 'mb-3' : ''"
            >
            <p class="chip" :class="$vuetify.breakpoint.mdAndDown ? 'mb-3' : ''"
>Meal card</p>
            <img
              height="100"
              src="../static/images/card2.png"
            >
          </div>

          <v-card-text class="section__benefits-title">Everything you desire in a single tap</v-card-text>

          <v-card-text class="section__benefits-text">Our reloadable gift card is the perfect gift to reward, to incentivise, to celebrate!</v-card-text>

          <v-card-text class="section__benefits-text--tip">Tax exemption: 300 euros per year per employee</v-card-text>

          <div class="section__benefits-text--list">
            <p class="title">Benefits</p>
            <p class="list--item"><v-icon class="icon">mdi-check-bold</v-icon> Order & load cards online in seconds, download invoices & reports in a click</p>
            <p class="list--item"><v-icon class="icon">mdi-check-bold</v-icon> Buy everything you want - electronics, clothing, cosmetics and so much more</p>
            <p class="list--item"><v-icon class="icon">mdi-check-bold</v-icon> Our app is loaded with crazy-fun features</p>
          </div>
        </div>

          <v-card-actions class="section__fourth-action section__benefits-action">
            <button
              @click="scrollToTellMeMoreSection"
              class="section__fourth-btn section__benefits-btn"
            >
              Tell me more 
              <v-icon class="icon">mdi-arrow-right-bold-outline</v-icon>
            </button>
          </v-card-actions>
        </v-card>
      </v-col>
    </div>
    <testimonials></testimonials>
    <v-col :class="$vuetify.breakpoint.lgAndUp ? 'pa-16' : ''" justify="center" align="center" cols="12" class="section__form" ref="contactUsSection">
      <h1 class="section__form-title">I am interested in getting the benefits of <span>Up Hellas</span></h1>
      <v-form
        ref="form"
        v-model="valid"
        lazy-validation
      >
        <div class="form-group py-16">
          <div class="form-field">
            <label for="fullname">Name & Surname</label>
            <v-text-field
              id="fullname"
              v-model="fullname"
              :rules="nameRules"
              required
            ></v-text-field>
          </div>
          <div class="form-field">
            <label for="fullname">Email</label>
            <v-text-field
              id="email"
              v-model="email"
              :rules="emailRules"
              required
            ></v-text-field>
          </div>
          <div class="form-field">
            <label for="phone">Phone</label>
            <v-text-field
              id="phone"
              v-model="phone"
              :rules="phoneRules"
              :counter="10"
              required
            ></v-text-field>
          </div>
          <div class="form-field">
            <label for="product">Product</label>
            <v-select
              id="product"
              v-model="selectedProduct"
              :items="products"
              :rules="[v => !!v || 'Product is required']"
              required
            ></v-select>
          </div>
          <div class="form-checkbox">
            <v-checkbox
              id="checkbox"
              v-model="checkbox"
              :rules="[v => !!v || 'You must agree to continue!']"
              required
            ></v-checkbox>
            <label for="checkbox">Επιθυμώ να χρησιμοποιηθούν τα παραπάνω στοιχεία μου από την Up Hellas, προκειμένου να ενημερωθώ για τα προϊόντα της, βάσει και του Γενικού Κανονισμού για την Προστασία Προσωπικών Δεδομένων που ισχ'υει από 25/5/2018</label>
          </div>
          <div class="form-btns">
            <v-btn
              :disabled="!valid"
              class="mr-4"
              @click="submit"
            >
              send us your message
            </v-btn>
            <p class="divider">or</p>
            <div class="pa-0 ma-0 section__second-cards">
              <v-menu
                v-model="datePickerVisible"
                :close-on-content-click="false"
                transition="scale-transition"
                offset-y
                min-width="auto"
              >
                <template v-slot:activator="{ on }">
                  <v-btn v-on="on">
                    Pick a Date
                  </v-btn>
                </template>
                <v-date-picker v-model="selectedDate" @input="saveSelectedDateAndClose" :min="minDate"></v-date-picker>
              </v-menu>
            </div>
          </div>
        </div>
      </v-form>
    </v-col>
  </v-row>
</template>
<style lang="scss">
  .logo {
    height: 150px;
    width: 150px;
  }

  .badge {
    position: absolute;
    right: 60%;
    z-index: 1;
    top: 130px;
  }

  .chip {
    padding: 1px 10px !important;
    border-radius: 50px;
    font-family: 'cfastystd-bold-webfont', sans-serif;
    font-size: 12px;
    text-transform: uppercase;
    margin: 0 80px 0 0 !important;
  }

  .section {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    width: 100%;

    &--left {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }

    &__title {
      font-family: 'FreeScript-Bold', sans-serif;
      font-size: 32px;
      color: #45C8FF;
      text-shadow: -5px 0 #7A4E1D;
      text-align: left;
      transform: rotate(-10deg);
      margin: 20px 0;
      text-transform: uppercase;
      align-self: flex-start;
    }

    &__paragraph {
      font-family: 'cfastystd-bold-webfont', sans-serif;
      font-size: 48px;
      text-align: left;
      padding: 0 0 0 35px;
      float: left;
      margin: 40px;
    }

    &__img {
      max-height: 100%;
      max-width: 100%;
    }

    &__btn {
      text-transform: uppercase;
      font-family: 'cfastystd-bold-webfont', sans-serif;
      margin: 40px 0;
      color: #303644;
      background-color: #ffffff;
      padding: 20px;
      font-size: 24px;
      border-radius: 50px;
      border: solid #303644;
      border-width: 2px 2px 6px 6px;
      align-self: flex-start;
    }

    &__scroll {
      color: #303644;
      text-transform: uppercase;
      font-family: 'cfastystd-bold-webfont', sans-serif;
      font-size: 14px;

      &-icon {
        font-size: 32px !important;
      }
    }

    &__second {
      &-subinfo {
        font-family: 'cfastystd-light-webfont', sans-serif;
        font-size: 24px;
        text-align: center;
        white-space: nowrap;
        font-weight: 600;
      }

      &-title {
        font-family: 'cfastystd-bold-webfont', sans-serif;
        font-size: 48px;
        text-align: center;
      }

      &-cards {
        justify-content: center;
        align-items: center;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
      }
    }

    &__benefits {
      padding: 40px 12px !important;

      &-card {
        border-radius: 30px !important;
        border: solid #303644;
        border-width: 2px 2px 6px 6px;
        background-color: #ffffff !important;
        margin: 60px 0 0 0;

        &-title {
          display: flex;
          flex-direction: row;
          justify-content: space-between;
          align-items: center;
        }
      }

      &-title {
        color: #303644;
        font-family: 'cfastystd-bold-webfont', sans-serif;
        font-size: 32px;
        text-align: left;
        line-height: 1.2;
      }

      &-text {
        color: #303644;
        font-family: 'cfastystd-light-webfont', sans-serif;
        font-size: 18px;
        text-align: left;
        font-weight: 700;

        &--tip {
          color: #303644;
          font-family: 'cfastystd-bold-webfont', sans-serif;
          font-size: 16px;
          text-align: left;
          padding: 10px 10px 10px 20px;
          background-color: #F0F0F0;
          border-radius: 10px;
        }

        &--list {
          margin-top: 20px;

          .title {
            color: #303644;
            font-family: 'cfastystd-bold-webfont', sans-serif !important;
            font-size: 18px !important;
            text-align: left;
            text-transform: uppercase;
            margin-bottom: 12px !important;
          }

          .list--item {
            text-align: left;
            color: #303644;
            font-family: 'cfastystd-light-webfont', sans-serif !important;
            font-size: 16px !important;
            font-weight: 700;
          }

          .icon {
            color: #45C8FF;
            padding: 1px;
            font-size: 15px !important;
            border-radius: 50% !important;
            border: 2px solid #303644;          
          }
        }
      }

      &-action {
        display: flex;
        flex-direction: row;
        justify-content: flex-end;
        align-items: center;
        padding: 0 !important;

        .section__benefits-btn {
          display: flex;
          flex-direction: row;
          justify-content: center;
          align-items: center;
          text-align: left;
          color: #ffffff;
          font-family: 'cfastystd-bold-webfont', sans-serif !important;
          font-size: 16px !important;
          text-transform: uppercase;
          border-radius: 20px 20px 20px 0 !important;
          border: solid #303644;
          border-width: 2px 2px 2px 6px;
          padding-left: 20px;

          .icon {
            padding: 10px 20px 15px 10px;
            color: #ffffff;
            font-size: 26px !important;
          }
        }
      }
    }

    &__third {
      background-color: #F9BB32 !important;

      .chip {
        background-color: #F79018;
      }

      &-action {

        .section__third-btn {
          background-color: #F79018;
        }
      }
    }

    &__fourth {
      background-color: #EE5A5A !important;

      .chip {
        background-color: #EE5A5A;
      }

      &-action {

        .section__fourth-btn {
          background-color: #EE5A5A;
        }
      }
    }

    &__form {
      background-color: #45C8FF;

      &-title {
        color: #303644;
        font-family: 'cfastystd-bold-webfont', sans-serif !important;
        font-size: 32px !important;

        span {
          color: #F79018;
        }
      }
    }
  }

  .card {
    background-color: #FACA92 !important;
    border-radius: 30px !important;
    border: solid #303644;
    border-width: 2px 2px 6px 6px;

    &.hovered-card {
      background-color: #ffffff !important;
    }

    &__title-image {
      margin: 20px 0;
    }

    &__title-text {
      color: #303644 !important;
      font-family: 'cfastystd-light-webfont', sans-serif;
      font-size: 18px;
      text-align: center;
      font-weight: 600;
    }

    &__button {
      background-color: #FACE3D !important;
      color: #303644 !important;
      font-family: 'cfastystd-bold-webfont', sans-serif;
      font-size: 16px !important;
      border-radius: 20px 20px 0 0 !important;
      border: solid #303644;
      border-width: 2px 2px 2px 6px;
      padding: 20px 40px !important;
      position: absolute;
      bottom: 0;
      left: 50px;
    }

    &__content {
      .card__button {
        opacity: 0;
        visibility: hidden;

        &.show-button {
          opacity: 1;
          visibility: visible;
        }
      }
    }
  }

  .form {
    &-group {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
    }

    &-field {
      margin: 0 20px;
      display: flex;
      flex-direction: column;
      align-items: flex-start;
    }

    &-checkbox {
      display: flex;
      flex-direction: row;
      justify-content: center;
    }

    &-btns {
      display: flex;
      flex-direction: row;
      justify-content: center;
      align-items: center;
    }
  }

  .divider {
    margin: 0 40px !important;
  }

  @media only screen and (max-width: 960px) {
    .badge {
      right: 10%;
      width: 100px;
      height: 100px;
      top: 100px;
    }

    .chip {
      margin: 0 !important;
    }

    .section {
      flex-direction: column;

      &__paragraph {
        margin: 20px;
        padding: 0;
      }

      &__second-subinfo {
        white-space: break-spaces;
      }

      &__benefits {

        &-card {

          &-title {
            display: flex;
            flex-direction: column;
          }
        }
      }
    }
  }

  @media only screen and (min-width: 961px) and (max-width: 1260px) {
    .badge {
      right: 50%;
    }

    .section {
      &__second-subinfo {
        white-space: break-spaces;
      }
    }
  }
</style>

<script>
import testimonials from '~/components/testimonials.vue';

export default {
  name: 'IndexPage',
  components: {
    'my-component': testimonials,
  },
  data () {
    return {
      cardsInfo: [
        {
          titleImg: 'go-for-eat.svg',
          title: 'The unrivalled meal card solution',
          img: '1.png',
          isHovered: false,
        },
        {
          titleImg: 'UP-GIFT.svg',
          title: 'The perfect gift',
          img: '2.png',
          isHovered: false,
        },
        {
          titleImg: 'up-cheque.svg',
          title: 'Where it all started; our meal vouchers',
          img: '3.png',
          isHovered: false,
        },
        {
          titleImg: 'up-holidays.svg',
          title: 'The card that takes you places',
          img: '4.png',
          isHovered: false,
        },
        {
          titleImg: 'up-fit.svg',
          title: 'The multi-gym membership',
          img: '5.png',
          isHovered: false,
        }
      ],
      valid: true,
      fullname: "",
      email: "",
      phone: "",
      selectedProduct: null,
      products: [
        'Up Go for Eat',
        'Up Gift',
        'Up Cheque Dejeuner',
        'Up Holidays',
        'Up Fit'
      ],
      checkbox: false,
      nameRules: [
        v => !!v || 'Name is required',
      ],
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      phoneRules: [
        v => !!v || 'Phone is required',
        v => /^[0-9]+$/.test(v) || 'Phone must contain only numbers',
        v => (v && v.length === 10) || 'Phone must be exactly 10 digits long',
        v => (v && v.startsWith('69')) || 'Phone must start with "69"',
      ],
      datePickerVisible: false, 
      selectedDate: null,
    }
  },
  methods: {
    isHovered(index) {
      this.cardsInfo[index].isHovered = true;
    },
    isNotHovered(index) {
      this.cardsInfo[index].isHovered = false;
    },
    scrollToCardsSection() {
      const cardsSection = this.$refs.cardsSection;

      if (cardsSection) {
        const yOffset = cardsSection.offsetTop;
        window.scrollTo({ top: yOffset, behavior: 'smooth' });
      }
    },
    scrollToTellMeMoreSection() {
      const contactUsSection = this.$refs.contactUsSection;

      if (contactUsSection) {
        const yOffset = contactUsSection.offsetTop;
        window.scrollTo({ top: yOffset, behavior: 'smooth' });
      }
    },
    submit () {
      this.$refs.form.validate();
      let payload = {};
      if (this.selectedDate !== null) {
        payload = {
          fullname: this.fullname,
          email: this.email,
          phone: this.phone,
          product: this.selectedProduct,
          checkbox: this.checkbox,
          selectedDate: this.selectedDate
        };
      } else {
        payload = {
          fullname: this.fullname,
          email: this.email,
          phone: this.phone,
          product: this.selectedProduct,
          checkbox: this.checkbox
        };
      }

      console.log(payload);
      //then we make the post or patch call to send the data of the form with a promise if success show success message else show error
    },
    openDatePicker() {
      this.datePickerVisible = true;
    },
    saveSelectedDateAndClose() {
      this.datePickerVisible = false;
      console.log("Selected date:", this.selectedDate);
      this.submit();
    },
  },
  computed: {
    cardImages() {
      return this.cardsInfo.map((card) => ({
        titleImg: require(`~/static/images/${card.titleImg}`),
        title: card.title,
        img: require(`~/static/images/${card.img}`),
        isHovered: card.isHovered,
      }));
    },
    minDate() {
      const currentDate = new Date();
      const year = currentDate.getFullYear();
      const month = (currentDate.getMonth() + 1).toString().padStart(2, '0');
      const day = currentDate.getDate().toString().padStart(2, '0');
      return `${year}-${month}-${day}`;
    },
  },
}
</script>