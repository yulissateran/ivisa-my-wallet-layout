<template lang="html">
  <div class="add-card">
    <div class="add-card__title">
      <h2>+ Add new card</h2>
    </div>
    <div class="add-card__body">
      <div class="add-card__header">
        <div class="add-card__description">
          <img src="../assets/images/ok-green-ico.svg" alt />
          <p class>We Accept All Major Debit / Credit Cards</p>
        </div>
        <div class="add-card__pay-methods">
          <img src="../assets/images/payment-methods-copy.jpg" alt />
        </div>
      </div>

      <form>
        <div class="form__body">
          <label for="cardName" class="control-lg">
            Name on Card
            <input
              v-bind:class="{ 'has-error': controls.name.invalid }"
              ref="name"
              v-model="controls.name.value"
              type="text"
              id="cardName"
            />
            <small class="invalid-feedback" v-if="controls.name.invalid">
              {{ errorMessage }}
            </small>
          </label>
          <label for="cardNumber" class="control-lg">
            Credit / Debit Card Number
            <input
              ref="number"
              v-model="controls.number.value"
              id="cardNumber"
              type="text"
            />
          </label>
          <label for="expMonth" class="control-sm">
            Exp. Month
            <select
              ref="expMonth"
              v-model="controls.expMonth.value"
              id="expMonth"
            >
              <option hidden value></option>
              <option value="value">value</option>
            </select>
          </label>
          <label for="expYear" class="control-sm">
            Exp. Year
            <input
              ref="expYear"
              v-model="controls.expYear.value"
              type="text"
              id="expYear"
            />
          </label>
          <label for="securityCode" class="control-sm">
            Security code
            <input
              ref="securityCode"
              v-model="controls.securityCode.value"
              type="text"
            />
          </label>
        </div>
        <div class="form__footer">
          <img
            class="security-icon"
            height="36px"
            width="95px"
            src="../assets/images/sectigo-trust-logo.png"
            alt
          />
          <button v-on:click="addCard" type="button">Submit payment</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script lang="js">
  export default  {
    name: 'src-components-add-card',
    props: [],
    mounted () {

    },
    data () {
      return {
       errorMessage: 'Field required',
       card: {
         number: null,
         name: '',
         expYear: null,
         expMonth: null,
         securityCode: null,
       },
       form: {
         errors: [],
         controls: {
          name: {
           required: true,
           value: '',
           errors: null,
           invalid: false,
         },
         number: {
           required: true,
           value: null,
           errors: null,
         },
        expMonth: {
           required: true,
           value: null,
           errors: null,
         },
         expYear: {
           required: true,
           value: null,
           errors: null,
         },
         securityCode: {
           required: true,
           value: null,
           errors: null,
         },
         }
       }
      }
    },
    methods: {
      validateCardNumber(){
        if(this.controls.number.value.length){
          this.$refs.number
        }
        
      }
      getInvalidControl(){
      return this.nameControls.find(control=>
        this.controls[control].required &&
        !this.controls[control].value);
      },

      setControlError(control){
        this.nameControls.forEach(nameControl => {
          if(control !== nameControl){
            this.controls[nameControl].invalid = false;
            this.controls[nameControl].errors = null;
          } else {
            this.controls[nameControl].invalid = true;
            this.controls[nameControl].errors = {};
            this.controls[nameControl].errors.required = true;
            this.$refs[nameControl].focus();
          }
        });
      },


     addCard() {
       const invalidControl = this.getInvalidControl();
       if(invalidControl){
         this.setControlError(invalidControl);
       } else {
          this.$emit('addCard', this.card);
          alert('add card');
       }
     }

    },
    computed: {
   controls(){
     return this.form.controls
   },
   nameControls(){
    return Object.keys(this.controls)
   }
    }
}
</script>

<style scoped lang="scss">
@import "../assets/styles/variables-grid.scss";
@import "../assets/styles/variables.scss";
@import "../assets/styles/text.scss";
@import "../assets/styles/buttons.scss";
.invalid-feedback {
  color: $error-color;
  position: absolute;
  bottom: -15px;
  left: 5px;
}

.add-card {
  margin-top: 13px;
  box-shadow: $box-shadow;
  border-radius: $size-radius-card;
}
.add-card__title {
  padding: 20px 25px;
}
.add-card__title > h2 {
  @extend .light-title;
}
.add-card__body {
  padding: 26px 25px;
  border-top: $border-light;
}
.add-card__header {
  margin-bottom: 10px;
}
.add-card__description {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 0 0 7px;
}
.add-card__pay-methods {
  margin: 18px 0 0 0;
  display: flex;
  justify-content: center;
}
.add-card__pay-methods img {
  width: 100%;
  height: 45px;
  max-width: 250px;
}
.add-card__description > p {
  color: $green;
  max-width: 180px;
  padding-left: 15px;
  text-align: start;
  font-size: 15.5px;
  line-height: 1.2;
  text-align: start;
}
.add-card__description img {
  width: 34px;
  height: 35px;
}

.form__body {
  font-size: 12.5px;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form__body input,
.form__body select {
  height: 39px;
  display: block;
  width: 100%;
  border: $border-dark;
  border-radius: $size-radius-card;
  margin-top: 10px;
}
.form__body input.has-error,
.form__body select.has-error {
  border: $border-error;
}
.form__body input:focus.has-error,
.form__body select:focus.has-error {
  outline: none;
  border: $border-error;
}

label {
  font-size: 14px;
  font-family: $font-family-secondary;
  text-align: start;
  display: block;
  width: 100%;
  margin-top: 15px;
  position: relative;
}
.form__footer {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.security-icon {
  margin: 20px 0 10px 0;
}
form button {
  @extend .main-button;
}
@media only screen and (min-width: map-get($breakpoints, md)) {
  .form__body {
    display: flex;
    flex-direction: row;
  }
  .form__body label + label {
    margin-left: 15px;
  }
  .form__footer {
    flex-direction: row;
    align-items: center;
    margin-top: 20px;
  }
  .security-icon {
    margin: 0 20px 0 0;
  }
  .control-lg {
    flex: 2;
  }
  .form__body .control-sm {
    flex: 1;
  }
  .add-card__header {
    display: flex;
    margin-bottom: 35px;
  }
  .add-card__pay-methods {
    margin-top: 0;
  }
  .add-card__description {
    margin: 0;
  }
}
</style>
