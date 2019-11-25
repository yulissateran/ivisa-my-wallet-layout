/*this is a single file component , the navigator don´t know it
for that, the CLI do it*/

<template class="">
  <div class="container">
    <div class="nav">
      <div class="wrapper">
        <div class="nav__item">
          <img src="../assets/images/my-applications-ico.svg" alt />
          <span>My applications</span>
        </div>
        <div class="nav__item">
          <img src="../assets/images/my-travelers-ico.svg" alt />
          <span>My travelers</span>
        </div>
        <div class="nav__item nav__item--active">
          <img src="../assets/images/my-cards-ico.svg" alt />
          <span>My cards</span>
        </div>
        <div class="nav__item">
          <img src="../assets/images/my-account-ico.svg" alt />
          <span>My account</span>
        </div>
      </div>
    </div>
    <div class="wrapper">
      <div class="wallet">
        <div class="wallet__cards">
          <div class="title">
            <h2>{{ msg }}</h2>
          </div>
          <div class="container-cards">
         
          </div>
        </div>
      </div>
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
                <input type="text" id="cardName" />
              </label>
              <label for="cardNumber" class="control-lg">
                Credit / Debit Card Number
                <input id="cardNumber" type="text" />
              </label>
              <label for class="control-sm">
                Exp. Month
                <select name id>
                  <option hidden value></option>
                  <option value="value">value</option>
                </select>
              </label>
              <label for class="control-sm">
                Exp. Year
                <input type="text" />
              </label>
              <label for class="control-sm">
                Security code
                <input type="text" />
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
              <button class>Submit payment</button>
            </div>
          </form>
        </div>
      </div>
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
@import "../assets/styles/variables.scss";
@import "../assets/styles/reset.scss";
@import "../assets/styles/buttons.scss";
@import "../assets/styles/text.scss";

.container {
  padding: 0 10px;
}

.nav {
  border-bottom: $border-light;
}
.nav > .wrapper {
  display: flex;
  justify-content: space-around;
}
.nav__item {
  position: relative;
  bottom: -1px;
  border: $border-light;
  padding: 10px 20px;
  opacity: 0.5;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.nav__item span {
  display: none;
}
.nav__item img {
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
label {
  font-size: 14px;
  font-family: $font-family-secondary;
  text-align: start;
  display: block;
  width: 100%;
  margin-top: 15px;
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

.wallet__cards {
  margin-top: 50px;
  box-shadow: $box-shadow;
  border-radius: $size-radius-card;
}

.container-cards {
  padding: 10px;
}
.title {
  padding: 25px;
  border-bottom: $border-light;
}
.title > h2 {
  @extend .light-title;
}





@media only screen and (min-width: map-get($breakpoints, md)) {
  .wrapper {
    max-width: map-get($container-max-widths, md);
    margin: 0 auto;
  }

  .container-cards {
    padding: 16px 25px;
  }
  .card {
    padding: 17px 35px;
  }
  .card__icon {
    align-items: center;
    img {
      position: initial;
    }
  }
  .card__body {
    flex-direction: row;
    padding-left: 25px;

    .description {
      margin: 0;
      margin-left: 15px;
    }
    .actions {
      flex: 2;
      justify-content: flex-end;
      align-items: center;
    }
    .actions button:first-child {
      margin-right: 20px;
    }
  }

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

@media only screen and (min-width: map-get($breakpoints, lg)) {
  .wrapper {
    max-width: map-get($container-max-widths, lg);
    margin: 0 auto;
  }
  .nav__item span {
    display: block;
    text-transform: uppercase;
    font-size: 12px;
    font-weight: bold;
    margin-left: 10px;
  }
}
</style>
