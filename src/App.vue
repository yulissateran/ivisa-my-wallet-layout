<template>
  <div id="app">
    <!-- <HelloWorld msg="My cards"/> -->
    <!-- <Modal type="changeToDefault"  v-on:close="closeModal" /> -->
    <!-- <Modal typeAction="remove" /> -->
    <Card  />

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import Modal from './components/Modal.vue'
import Card from './components/Card.vue'

export default {
  name: 'app',
  components: {
    // HelloWorld,
    // Modal,
Card
  }, 
  methods: {
    closeModal(){
      alert('CLOSE EMIT!!');
    }
  }    

}
</script>

<style>
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

</style>
