/*this is a single file component , the navigator don´t know it
for that, the CLI do it*/

<template class="">
  <div class="container">
    <div class="container-modal">
      <div>
    <div class="modal">
        <div class="modal__header">
          <span>&#10006;</span>
        </div>
        <div class="modal__body">
          <img class="icon" src="../assets/images/default-card-ico.svg" alt="">

        </div>
        <div class="modal__footer">
          
        </div>
      </div>
      </div>
  
    </div>
    <div class="nav">
      <div class="nav__item"><img src="../assets/images/my-applications-ico.svg" alt=""></div>
      <div class="nav__item"><img src="../assets/images/my-travelers-ico.svg" alt=""></div>
      <div class="nav__item nav__item--active"><img src="../assets/images/my-cards-ico.svg" alt=""></div>
      <div class="nav__item"><img src="../assets/images/my-account-ico.svg" alt=""></div>
    </div>
    <div class="wallet__cards">
      <div class="title">
        <h2>{{ msg }}</h2>
      </div>
      <div class="container-cards">
        <div class="card">
          <div class="card__icon">
            <!-- <img class="ok-icon" src="../assets/images/ok-grey-ico.svg" alt /> -->
            <img class="ok-icon" src="../assets/images/ok-green-ico.svg" alt />
          </div>
          <div class="card__body">
            <div class="container-img">
              <img src="../assets/images/visa-card-logo.svg" alt />
            </div>
            <div class="description">
              <span
                class="description__title"
              >American Express &#8226;&#8226;&#8226;&#8226; &#8226;&#8226;&#8226;&#8226; &#8226;&#8226;&#8226;&#8226; 7015</span>
              <span class="description__subtitle">Ex.Date: 10/2023</span>
            </div>
            <div class="actions">
              <button class="actions__button actions__button--remove">Remove</button>
              <button class="actions__button actions__button--default">Default</button>
            </div>
          </div>
        </div>

           <div class="card">
          <div class="card__icon">
            <!-- <img class="ok-icon" src="../assets/images/ok-grey-ico.svg" alt /> -->
            <img class="ok-icon" src="../assets/images/ok-green-ico.svg" alt />
          </div>
          <div class="card__body">
            <div class="container-img">
              <img src="../assets/images/visa-card-logo.svg" alt />
            </div>
            <div class="description">
              <span
                class="description__title"
              >American Express &#8226;&#8226;&#8226;&#8226; &#8226;&#8226;&#8226;&#8226; &#8226;&#8226;&#8226;&#8226; 7015</span>
              <span class="description__subtitle">Ex.Date: 10/2023</span>
            </div>
            <div class="actions">
              <button class="actions__button actions__button--remove">Remove</button>
              <button class="actions__button actions__button--default">Default</button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="add-card">
      <div class="add-card__title">
        <h2>+ Add new card</h2>
      </div>
      <!-- <div class="add-card__body">
        <div class="add-card__description">
          <img src="../assets/images/ok-green-ico.svg" alt />
          <p class>We Accept All Major Debit / Credit Cards</p>
        </div>
        <div class="add-card__pay-methods">
          <img src="../assets/images/payment-methods-copy.jpg" alt />
        </div>
        <form class>
          <div class="form__body">
            <label for>Name on Card</label>
            <input type="text" />
            <label for>Credit / Debit Card Number</label>
            <input type="text" />
            <label for>Exp. Month</label>
            <select name id>
              <option hidden value></option>
              <option value="value">value</option>
            </select>
            <label for>Exp. Year</label>
            <input type="text" />
            <label for>Security code</label>
            <input type="text" />
          </div>
          <div class="form__footer">
            <img class="security-icon" 
            height="36px" 
            width="95px" 
            src="../assets/images/sectigo-trust-logo.png" alt />
            <button class="" >Submit payment</button>
          </div>
        </form>
      </div> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style  lang="scss">
// <style scoped lang="scss">
$second-blue-ref: #43689e;
$gray-ref: #ededed;
$second-blue: #5b73c1;
$black-blue: #2c3143;
$green: #52d03e;
$dark-gray: #6a757e;
$gray: #f7f8f9;
$dark-green: #0ca52f;
$size-radius: 6px;
$size-radius-buttons: 6px;
$size-radius-card: 3px;
$dark-light-gray: #dae1e7;
// $ttt2 : #878892;
$padding-card-y: 15px;
$padding-card-x: 12px;
$font-family-main: "Open Sans", sans-serif;
$font-family-secondary: "Roboto", sans-serif;
$border-light: 1px solid $gray;
$border-dark: .5px solid $dark-gray;
$box-shadow: 0 0 5px 3px $gray-ref, 0 0 5px 10px $gray;
input,
button {
  outline: none;
}
body,
html,
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: $font-family-main;
  color:$dark-gray;
}

button {
  cursor: pointer;
}
.container {
  // margin: 80px 0;
}

.light-title {
  font-weight: normal;
  font-size: 1.5em;
  text-align: start;
  color: $second-blue;
}

.container-modal {
 z-index: 1000;
 position: fixed;
}
.container-modal >div {
   height: 100vh;
 width: 100vw;
 background-color: rgba(44,49,67,.5);
 top:0;
 bottom: 0;
 display: flex;
 justify-content: center;
 align-items: center;
}
.modal {
 background-color: white;
 max-width: 360px;
 width: 100%;
 height: auto;
 border-radius: 3px;
 padding: 10px 20px;
 margin: 0 10px;
}
.modal__header span {
  font-size: 25px;
}
.modal .icon {
  height: 85px;
  width: 105px;
  margin: 20px 0 0 20px;
}


.nav {
  display: flex;
  justify-content: space-around;
  border-bottom:  $border-light;
}
.nav__item {
  position: relative;
  bottom: -1px;
  border: $border-light;
  padding: 10px 20px;
  opacity: .5;
}
.nav__item  img {
  height: 30px;
  width: 30px;
}

.nav .nav__item--active {
  border-bottom: 1px solid white;
  border-top: 2px solid $dark-green;
  opacity: 1;
}



.add-card {
  margin-top: 13px;
  box-shadow: $box-shadow;
}
.add-card__title {
  padding: 20px 21px;
}
.add-card__title > h2 {
  @extend .light-title;
}
.add-card__description {
  color: $green;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 0 0 7px;
}
.add-card__pay-methods {
  margin: 18px 0 0 0;
}
.add-card__pay-methods img {
  width: 100%;
  height: 45px;
  max-width: 250px;
}
.add-card__description > p {
  max-width: 180px;
  padding-left: 15px;
  text-align: start;
  font-size: 15.5px;
  line-height: 1.2;
  text-align: start;
}
.add-card__description img {
  // padding-left: 15px;
  width: 34px;
  height: 35px;
}
.add-card__body {
  padding: 26px 28px;
  border-top: $border-light;
}

.form__body {
  font-size: 12.5px;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form__body > input,
.form__body > select {
  height: 39px;
  display: block;
  width: 100%;
  border: $border-dark;
  border-radius: 3px;
}
.form__footer button{
  padding: 10px 0;
  font-weight: bold;
  font-size: 18px;
  border-radius: 6px;
}
.security-icon {
  margin: 20px 0 10px 0;
}
form button {
  background-color: $green;
  color: white;
  border: none;
  padding: 10px 25px;
  width: 100%;
  border-radius: 6px;
}
label {
      font-size: 14px;
      font-family: $font-family-secondary;
  text-align: start;
  display: block;
  width: 100%;
  margin-bottom: 5px;
  margin-top: 15px;
}

.wallet__cards {
  margin-top: 50px;
  box-shadow: $box-shadow;
}

.container-cards {
  padding: 10px;
}
.title {
  padding: 10px;
  border-bottom: $border-light;
}
.title > h2 {
  @extend .light-title;
}

.card {
  width: 100%;
  display: flex;
  background-color: $gray;
  padding-top: $padding-card-y;
  padding-bottom: $padding-card-y;
  padding-left: $padding-card-x;
  padding-right: $padding-card-x;
  border-top-left-radius: $size-radius-card;
  border-top-right-radius: $size-radius-card;
}
.card + .card {
  margin-top: 10px;
}
.card__icon {
  display: flex;
  justify-content: center;
}
.card__icon > img {
  position: relative;
  height: 19px;
  width: 19px;
  top: 15px;
}
.card__body {
  display: flex;
  flex: 1;
  flex-direction: column;
  padding-left: 15px;
  .container-img {
    display: inherit;
    justify-content: start;
  }
  .container-img > img {
    height: 40px;
  }
  .description {
    font-weight: normal;
    display: flex;
    flex-direction: column;
    align-items: start;
    text-align: start;
    margin: 15px 0 20px 0;
    color: $dark-gray;
  }
  .description__subtitle {
    font-size: 12.5px;
  }
  .actions {
    padding-left: 5px;
    padding-right: 5px;
    display: flex;
    justify-content: space-between;
  }
  .actions__button {
    padding: 0;
    display: flex;
    justify-content: space-between;
    border: none;
    border-bottom: 2px solid $dark-light-gray;
    background: transparent;
    font-weight: bold;
    color: $dark-light-gray;
  }

  .actions__button--default {
    color: $second-blue;
  }
}
</style>
