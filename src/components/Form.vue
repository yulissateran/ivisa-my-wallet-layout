<template lang="html">
  <form >
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
        <small
          class="invalid-feedback"
          v-if="$v.name.$error && !$v.name.required"
        >
          {{ errorMessage }}
        </small>
      </label>
      <label for="cardNumber" class="control-lg">
        Credit / Debit Card Number
        <input
          v-bind:class="{ 'has-error': $v.number.$error }"
          ref="number"
          v-model="number"
          id="cardNumber"
          type="text"
          v-on:input="setNumberControl($event)"
        />
        <!-- v-on:keyup="setNumberControl($event)" -->
        <small
          class="invalid-feedback"
          v-if="$v.number.$error && !$v.number.required"
        >
          {{ errorMessage }}
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
          <option hidden value></option>
          <option v-for="month in expMonths" :value="month" :key="month">{{
            month
          }}</option>
        </select>
        <small
          class="invalid-feedback"
          v-if="$v.expMonth.$error && !$v.expMonth.required"
        >
          {{ errorMessage }}
        </small>
      </label>
      <label for="expYear" class="control-sm">
        Exp. Year
        <select
          v-bind:class="{ 'has-error': $v.expYear.$error }"
          ref="expYear"
          v-model="expYear"
          id="expYear"
        >
          <option hidden value></option>
          <option v-for="year in expYears" :value="year" :key="year">{{
            year
          }}</option>
        </select>
        <small
          class="invalid-feedback"
          v-if="$v.expYear.$error && !$v.expYear.required"
        >
          {{ errorMessage }}
        </small>
      </label>
      <label for="securityCode" class="control-sm">
        Security code
        <input
          v-bind:class="{ 'has-error': $v.securityCode.$error }"
          ref="securityCode"
          v-model="securityCode"
          type="text"
        />
        <small
          class="invalid-feedback"
          v-if="$v.securityCode.$error && !$v.securityCode.required"
        >
          {{ errorMessage }}
        </small>
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
      <button v-on:click="send" type="button">Submit payment</button>
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
    },
    data () {
      return {
        errorMessage: 'Field required',
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
          // '01| January',
          // '02| February',
          // '03| March',
          // '04| April',
          // '05| May',
          // '06| June',
          // '07| July',
          // '08| August',
          // '09| September',
          // '10| October',
          // '11| November',
          // '12| December'
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
        minLength: minLength(19),
        maxLength: maxLength(19),
        numeric
      },
      expMonth: {
        required,
      },
      expYear: {
        required,
      },
       securityCode: {
        required,
      }
    },
   methods: {
     reset(){
        this.$v.$reset()
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
       const firstInvalidControl = this.formControls.find(nameControl => this.$v[nameControl].$invalid);
       this.$refs[firstInvalidControl].focus();
       }
      },
      getOnlyNumbers(string){
        const iterableValue = string.split('');
          let newValue = '';
          iterableValue.forEach((character, index)=> {
            if(!isNaN(character)){
              newValue = newValue + character;
            }
          });
          return newValue;
      },
      // get
      setSpace(string){
          const positionOfSpaces = [4, 9, 14]
          const iterableValue = string.split('');
          let newValue = '';
          iterableValue.forEach((character, index)=> {
            if(positionOfSpaces.includes(index)){
              newValue = newValue + ' ';
            }
          });
          return newValue;
      },
      setNumberControl(event){
        // let value = this.number;
        // if(value){
        //   if(value.length >= 20){
        //     this.number = value.slice(0, 20)
        //   }
        //   value = this.number.split(' ').join('');
        //   value = this.getOnlyNumbers(value)
        //   value = this.setSpace(value)
        //   this.number = value;
        // }
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
  left: 5px;
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

.form__body input:focus,
.form__body select:focus {
  outline: none;
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
