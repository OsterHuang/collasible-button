<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />

    <CollapsibleButton />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import CollapsibleButton from "@/components/CollapsibleButton";

export default {
  name: "App",
  components: {
    HelloWorld,
    CollapsibleButton
  }
};
</script>

<style lang="stylus">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
