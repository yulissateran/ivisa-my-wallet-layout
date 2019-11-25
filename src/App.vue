<template>
  <!-- <div id="app"> -->
      <Main/>
  <!-- </div> -->
</template>

<script>
import Main from "./components/Main.vue";
export default {
  name: "app",
  components: {
    Main
  },
  methods: {
    closeModal() {
      alert("CLOSE EMIT!!");
    }
  }
};
</script>

<style>
@import "./assets/styles/grid.scss";

/* font-family: 'Roboto', sans-serif;
font-family: 'Open Sans', sans-serif; */
#app {
  /* font-family: 'Open Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}
.container {
  padding: 0 10px;
}
</style>
