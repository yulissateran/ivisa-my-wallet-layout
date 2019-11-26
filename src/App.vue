
/*this is a single file component , the navigator don´t know it for that, the
CLI do it*/<template>
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

.container {
  padding: 0 10px;
}
</style>
