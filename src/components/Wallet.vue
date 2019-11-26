<template class="">
  <div class="wrapper">
    <div class="wallet">
      <div class="wallet__cards">
        <div class="title">
          <h2>My Cards</h2>
        </div>
        <div v-if="cards.length" class="container-cards">
          <Card
            v-for="card in cards"
            :key="card.name"
            v-bind="{ ...card, defaultCardName }"
            v-on:remove="handleRemove"
            v-on:changeToDefault="handleChangeToDefault"
          />
        </div>
      </div>
      <Add-card v-on:newCard="addCard" />
    </div>
    <Modal
      v-if="modal.isVisible"
      v-bind="currentModal"
      v-on:close="closeModal"
      v-on:do="doActionInCard"
    />
  </div>
</template>

<script lang="js">
import Card from "./Card.vue";
import Modal from "./Modal.vue";
import AddCard from "./AddCard.vue";
/* eslint-disable */
  export default  {
    name: 'Wallet',
    components: {
    Card,
    AddCard,
    Modal
    },
    props: [],
    mounted () {

    },
    data () {
      return {
        defaultCardName: 'American Express',
        selectedCardName: null,
        currentModal: null,
        cards: [
          {
            name: 'American Express',
            number: '.... .... .... 4536',
            expMonth: '12',
            expYear: '2019',
            securityCode: 386,
          }
        ],
        modal: {
          isVisible: false,
          actions : {
            remove: {
            type: 'remove',
            title: 'Remove card',
            message: 'Are you sure you want to remove from wallet?',
            iconSource:'remove-payment-ico.svg',
            iconDescription:''
            },
            changeToDefault :{
              type: 'changeToDefault',
              title: 'Change default card',
              message: `This card will appear
                as a primary option for your payment.
                Are you sure you want
                to set this card
                as default?`,
              iconSource:'default-card-ico.svg',
              iconDescription:''
            }
          }
        }
      }
    },
    methods: {
       addCard(event){
         this.cards.push(event)
       },

       handleRemove(name){
        this.selectedCardName = name;
         this.openModal('remove')
       },
         handleChangeToDefault(name){
        this.selectedCardName = name;
         this.openModal('changeToDefault')
       },
       removeCard(name){
         this.cards = this.cards.filter(card=>card.name !== name);
       },
       changeToDefault(name){
         this.defaultCardName = name;
       },
       doActionInCard(action){
          switch (action) {
            case 'remove':
              this.removeCard(this.selectedCardName);
              break;
              case 'changeToDefault':
              this.changeToDefault(this.selectedCardName);
              break;
          }
          this.closeModal();
       },
       openModal(action){
         this.currentModal = this.modal.actions[action];
         this.$set(this.modal, 'isVisible', true)
       },
       closeModal(){
         this.modal.isVisible = false;
       }
    },
    computed: {

    }
}
</script>

<style scoped lang="scss">
@import "../assets/styles/grid.scss";
@import "../assets/styles/variables.scss";
@import "../assets/styles/reset.scss";
@import "../assets/styles/buttons.scss";
@import "../assets/styles/text.scss";

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
</style>
