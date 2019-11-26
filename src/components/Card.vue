<template lang="html">
  <div class="card">
    <div class="card__icon">
      <img v-if="isDefault" class="ok-icon" src="../assets/images/ok-green-ico.svg" alt="" />
      <img v-if="!isDefault" class="ok-icon" src="../assets/images/ok-grey-ico.svg" alt />
    </div>
    <div class="card__body">
      <div class="container-img">
        <img src="../assets/images/visa-card-logo.svg" alt />
      </div>
      <div class="description">
        <span class="description__title">{{name}} {{number}}</span>
        <span class="description__subtitle">Ex.Date: {{expMonth}}/{{expYear}}</span>
      </div>
      <div class="actions">
        <button v-on:click="handleRemove" class="actions__button actions__button--remove">Remove</button>
        <button v-on:click="handleChangeToDefault"  class="actions__button actions__button--default">
          Default
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="js">
/* eslint-disable */
  export default  {
    name: 'Card',
    props: [ 'name', 'number', 'expMonth','expYear', 'defaultCardName'],
    mounted () {
      console.log(this)
    },
    data () {
      return {
      }
    },
    methods: {
      handleChangeToDefault(){
        this.$emit('changeToDefault', this.name)
      },
      handleRemove(){
        this.$emit('remove', this.name)
      }
    },
    computed: {
      isDefault(){
        return this.defaultCardName === this.name;
      }
    }
}
</script>

<style scoped lang="scss">
@import "../assets/styles/variables.scss";
@import "../assets/styles/variables-grid.scss";
@import "../assets/styles/reset.scss";
// @import "../assets/styles/buttons.scss";
// @import "../assets/styles/text.scss";
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
    color: $dark-gray-light;
  }
  .description__subtitle {
    font-size: 12px;
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
    // border-bottom: 2px solid $dark-gray-light;
    background: transparent;
    font-weight: bold;
    color: $dark-light-gray;
    // color: $dark-gray-light;
  }

  .actions__button--default {
    color: $second-blue;
    // Boton subrayado Default: Open Sans Bold #5b73c1 (Active opacity 40%)
  }
  .actions__button:active {
    opacity: 40%;
  }
}
@media only screen and (min-width: map-get($breakpoints, md)) {
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
}
</style>
