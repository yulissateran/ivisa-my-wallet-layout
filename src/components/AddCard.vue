<template lang="html">
  <div class="add-card">
    <div v-on:click="showForm" class="add-card__title">
      <h2 >+ Add new card</h2>
    </div>
    <div class="add-card__body" v-if="isVisibleForm">
      <div class="add-card__header">
        <div class="add-card__description">
          <img src="../assets/images/ok-green-ico.svg" alt="check green icon" />
          <p class>We Accept All Major Debit / Credit Cards</p>
        </div>
        <div class="add-card__pay-methods">
          <img src="../assets/images/payment-methods-copy.jpg" alt />
        </div>
      </div>
     <Form v-on:send="newCard"/>
    </div>
  </div>
</template>

<script lang="js">
/* eslint-disable */

import Form from "./Form.vue";
  export default  {
    name: 'src-components-add-card',
    components: {
      Form
    },
    props: [],
    mounted () {

    },
    data () {
      return {
        isVisibleForm: false,
      }
    },
    methods: {
    newCard(event){
         this.$emit('newCard', event);
    },
    showForm(){
      this.isVisibleForm =  !this.isVisibleForm;
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

.add-card {
  margin-top: 13px;
  box-shadow: $box-shadow;
  border-radius: $size-radius-card;
}
.add-card__title {
  cursor: pointer;
  padding: 20px 25px;
}
.add-card__title > h2 {
  @extend .light-title;
}
.add-card__body {
  padding: 25px 20px;
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
@media only screen and (min-width: map-get($breakpoints, sm)) {
  .add-card__body {
    padding: 25px;
  }
}
@media only screen and (min-width: map-get($breakpoints, md)) {
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
