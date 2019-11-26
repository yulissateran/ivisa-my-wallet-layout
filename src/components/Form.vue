<template lang="html">


  <form v-on:submit="send">
    <div class="form__body">
      <label for="cardName" class="control-lg">
        Name on Card
        <input
          v-bind:class="{ 'has-error': $v.name.$error }"
          ref="name"
          v-model="name"
          type="text"
          id="cardName"
        />
      </label>
      <label for="cardNumber" class="control-lg">
        Credit / Debit Card Number
        <input
          v-bind:class="{ 'has-error': $v.number.$error }"
          ref="number"
          v-model="number"
          id="cardNumber"
          type="text"
          v-on:paste="setNumberControl"
          v-on:keyup="handleKeyUp"
          maxLength="19"
        />
        <small
          class="invalid-feedback"
          v-if="
            $v.number.$error &&
              !$v.number.min &&
              this.number &&
              this.number.length
          "
        >
          Card number is too short
        </small>
      </label>
      <label for="expMonth" class="control-sm">
        Exp. Month
        <select
          ref="expMonth"
          v-bind:class="{ 'has-error': $v.expMonth.$error }"
          v-model="expMonth"
          id="expMonth"
        >
          <!-- <option hidden value=""></option> -->
          <option v-for="month in expMonths" :value="month" :key="month">{{
            month
          }}</option>
        </select>
      </label>
      <label for="expYear" class="control-sm">
        Exp. Year
        <select
          v-bind:class="{ 'has-error': $v.expYear.$error }"
          ref="expYear"
          v-model="expYear"
          id="expYear"
        >
          <!-- <option hidden value=""></option> -->
          <option v-for="year in expYears" :value="year" :key="year">{{
            year
          }}</option>
        </select>
      </label>
      <label for="securityCode" class="control-sm">
        Security code
        <input
          v-bind:class="{ 'has-error': $v.securityCode.$error }"
          ref="securityCode"
          v-model="securityCode"
          type="text"
          v-on:input="formatSecurityCode"

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
      <button v-on:click="send" type="button">Add card</button>
    </div>
  </form>
</template>

<script lang="js">
/* eslint-disable */
import { required, minLength, numeric, maxLength  } from 'vuelidate/lib/validators'
  export default  {
    name: 'Form',
    props: [],
    mounted () {
      this.$refs.name.focus();
    },
    data () {
      return {
        formControls: [
          'name',
          'number',
          'expMonth',
          'expYear',
          'securityCode'
        ],
        expYears: [
         '2020',
         '2021',
         '2022',
         '2023',
         '2024',
         '2025',
         '2026',
         '2027',
         '2028',
         '2029',
         '2030',
         '2031',
         '2032',
         '2033',
         '2034',
         '2035',
         '2036',
         '2037',
         '2038',
        ],
        expMonths: [
          '01',
          '02',
          '03',
          '04',
          '05',
          '06',
          '07',
          '08',
          '09',
          '10',
          '11',
          '12'
        ],
        name: null,
        number: null,
        expMonth:null,
        expYear: null,
        securityCode: null,
      }
    },
    validations: {
      name: {
        required,
      },
  	  number: {
        required,
        minLength: minLength(16),
        maxLength: maxLength(19),
      },
      expMonth: {
        required,
      },
      expYear: {
        required,
      },
       securityCode: {
        required,
        numeric
      }
    },
    methods: {
      reset(){
        this.$v.$reset();
        this.name = null;
        this.number = null;
        this.expMonth = null;
        this.expYear = null;
        this.securityCode = null;
      },
      send() {
        this.$v.$touch();
        if(!this.$v.$invalid){
          this.$emit('send',
          {
            name: this.name,
            number: this.number,
            expMonth: this.expMonth,
            expYear: this.expYear,
            securityCode: this.securityCode,
          });
          this.reset();
        } else {
         this.$refs[this.getFirstInvalidControl()].focus();
        }
      },
      getFirstInvalidControl(){
        return this.formControls.find(nameControl => this.$v[nameControl].$invalid);
      },
      deleteSpaces(string){
        return string.split(' ').join('');
      },
      sliceCardNumber(string){
        if(string && string.length > 16) {
          string = string.slice(0,20);
        }
        return string;
      },
      getIterableString(string){
        return this.sliceCardNumber(this.deleteSpaces(string)).split('');
      },
      getCardNumberFormated(event, string){
          const iterableString = this.getIterableString(string);
          let cardNumberFormated = '';
          iterableString.forEach((character, index)=> {
            if(!isNaN(character)){
              if(index < 12 && (index + 1) % 4 === 0 ){
                cardNumberFormated += character + ' ';
              } else {
                cardNumberFormated += character ;
              }
            }
          });
          return cardNumberFormated;
      },
      setCardNumberFormated(event, string){
        if(event.keyCode !== 8 && string){
          this.number = this.getCardNumberFormated(event,string);
        }
      },
      setNumberControl(event){
        this.setCardNumberFormated(event, this.number)

      },
      handleKeyUp(event){
        this.setCardNumberFormated(event, this.number)
      },
      formatSecurityCode(){
            let formatedSecurityCode = '';
        this.getIterableString(this.securityCode).forEach(character=>{
          if(!isNaN(character)){
            formatedSecurityCode += character;
          }
          this.securityCode = formatedSecurityCode;
        })
      }
    },
    computed: {

    }
}
</script>
<style scoped lang="scss">
@import "../assets/styles/reset.scss";
@import "../assets/styles/variables-grid.scss";
@import "../assets/styles/variables.scss";
@import "../assets/styles/text.scss";
@import "../assets/styles/buttons.scss";
.invalid-feedback {
  color: $error-color;
  position: absolute;
  bottom: -15px;
  // font-weight: normal;
  left: 5px;
}
.form__body {
  font-size: 14px;
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
  border-radius: $size-radius-form-controls;
  margin-top: 10px;
  @extend .base-control;
}
.form__body select option {
  text-align: center;
}

.form__body input.has-error,
.form__body select.has-error {
  border: $border-error;
}

.form__body input.has-error:focus,
.form__body select.has-error:focus {
  outline: none;
  border: $border-error;
  box-shadow: $box-shadow-error;
}

label {
  font-weight: bold;
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
    font-size: 13.3px;
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
