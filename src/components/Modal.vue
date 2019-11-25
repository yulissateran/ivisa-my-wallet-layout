<template lang="html">
  <div class="container-modal">
    <div>
      <div class="modal">
        <div class="modal__header">
          <span v-on:click="close">&times;</span>
        </div>
        <div class="modal__body">
          <div class="modal__body--img">
            <img class="icon" :src="icon" :alt="action.iconDescription" />
          </div>
          <div class="modal__body--description">
            <span class="modal__body--title">
              {{ action.title }}
            </span>
            <p>
              {{ action.message }}
            </p>
          </div>
        </div>
        <div class="modal__footer">
          <button v-on:click="doAction" type="button" class="change-default">Yes</button>
          <button v-on:click="calcelAction"  type="button" class="cancel-change-default">Cancel</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="js">
  export default  {
    name: 'modal',
      props: {
        type: {
          type: String,
          default: 'remove',
          required: true,
          validator(value) {
            const permitedActions = ['remove', 'changeToDefault'];
          return permitedActions.indexOf(value) !== -1
      }
        },
  }
    ,
    // mounted () {

    // },
    data () {
      return {
      actions :{
      remove: {
      title: 'Remove card',
      message: 'Are you sure you want to remove from wallet?',
      iconSource:'remove-payment-ico.svg',
      iconDescription:''
      },
      changeToDefault :{
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
    },
    methods: {
     close() {
        this.$emit('close');
     },     
     calcelAction() {
       this.close();
     },
     doAction() {
        this.$emit(this.type);
      alert('doAction!!');
     }
    },
    computed: {
     action() {
      return this.actions[this.type]
     },
     icon() {
          return require('../assets/images/' + this.action.iconSource) // the module request
     }
    }
}
</script>

<style scoped lang="scss">
@import "../assets/styles/variables.scss";
@import "../assets/styles/reset.scss";
@import "../assets/styles/buttons.scss";
@import "../assets/styles/text.scss";
.container-modal {
  z-index: 1000;
  position: fixed;
}
.container-modal > div {
  height: 100vh;
  width: 100vw;
  background-color: rgba(44, 49, 67, 0.35);
  top: 0;
  bottom: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal {
  background-color: white;
  max-width: 335px;
  width: 100%;
  height: auto;
  border-radius: 3px;
  padding: 10px 25px 25px 25px;
  margin: 0 10px;
  margin-top: 50px;
}
.modal__header span {
  position: relative;
  line-height: 0.6;
  font-size: 45px;
  margin-left: -5px;
  top: 5px;
}
.modal__body {
  padding: 10px 17px 12px 17px;
}
.modal .icon {
  height: 85px;
  width: 105px;
}

.modal__body .modal__body--title {
  @extend .light-title;
  margin-top: 13px;
}

.modal__body p {
  margin-top: 3px;
  line-height: 1.2;
}
.modal__footer {
  display: flex;
  flex-direction: column;
}
.modal__footer button {
  @extend .base-button;
}
.modal__footer .change-default {
  @extend .main-button;
}
.cancel-change-default {
  @extend .secondary-button;
}

@media only screen and (min-width: map-get($breakpoints, sm)) {
  .modal__footer {
    flex-direction: row;
  }
  .modal__footer button:first-child {
    margin-right: 15px;
  }
  .modal__body {
    padding-left: 0;
    padding-right: 0;
  }
  .modal {
    max-width: 400px;
  }
}
</style>
