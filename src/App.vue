<template>
  <div id="app">
    <MainPage />
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import MainPage from "./components/MainPage";

@Component({
  components: {
    MainPage
  }
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 40px 30px;
}
</style>
