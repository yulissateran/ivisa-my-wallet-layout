<template class="">
      <div class="wrapper">
            <div class="wallet">
        <div class="wallet__cards">
          <div class="title">
            <h2>My Cards</h2>
          </div>
          <div class="container-cards">
            <Card />
          </div>
        </div>
        <Add-card/>
      </div>
        </div>
</template>

<script lang="js">
import Card from "./Card.vue";
import AddCard from "./AddCard.vue";

  export default  {
    name: 'src-components-wallet',
    components: {
    Card,
    AddCard
    },
    props: [],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

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
