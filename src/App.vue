<template>
  <div id="app">
    <Container/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Container from "@/components/Container.vue";

@Component({
  components: {
    Container,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
body {
  background-color: #35495e;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #42b883;
  margin-top: 60px;

}
</style>
