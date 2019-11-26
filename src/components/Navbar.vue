<template lang="html">
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
</template>

<script lang="js">

  export default  {
    name: 'components-navbar',
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
@import "../assets/styles/variables-grid.scss";
@import "../assets/styles/variables.scss";
@import "../assets/styles/reset.scss";
@import "../assets/styles/grid.scss";

.nav {
  border-bottom: $border-light;
  margin-top: 70px;
}
.nav > .wrapper {
  display: flex;
  justify-content: space-around;
}
.nav__item {
  position: relative;
  bottom: -1px;
  border: $border-light;
  padding: 10px 0;
  opacity: 0.5;
  display: flex;
  align-items: center;
  justify-content: center;
  flex: 1;
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


@media only screen and (min-width: map-get($breakpoints, sm)) {
  .nav__item {
    padding: 10px 20px;
  }
}
@media only screen and (min-width: map-get($breakpoints, lg)) {
  .nav__item span {
    display: block;
    text-transform: uppercase;
    font-size: 12px;
    font-weight: bold;
    margin-left: 10px;
    color: $black-blue;
  }
}
</style>
