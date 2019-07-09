<template>
  <div id="app">
    <!-- This is the root of your panel -->
    <!-- Content should go inside #app -->
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue CLI panel"/>
  </div>
</template>

<script>
// You can access this App.vue file from any other component via `this.$root.$children[0]`
// See `./components/HelloWorld.vue` for example of CSInteface and app

// Create your own components and import them here
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  components: {
    HelloWorld
  },
  data: () => ({
    csInterface: null
  }),
  mounted() {
    this.csInterface = new CSInterface();
  },
  methods: {
    dispatchEvent(name, data) {
      var event = new CSEvent(name, "APPLICATION");
      event.data = data;
      this.csInterface.dispatchEvent(event);
    },
    loadScript(path) {
      this.csInterface.evalScript(`$.evalFile('${path}')`);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
