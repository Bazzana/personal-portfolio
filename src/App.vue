<template>
  <div id="app">
    <Header/>
    <Section/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Section from "./components/Section.vue";

export default {
  name: "app",
  components: {
    Header,
    Section
  }
};
</script>

<style>
#app {
  font-family: "Open Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
div {
  box-sizing: border-box;
}
html {
  scroll-behavior: smooth;
}
.header {
  display: none;
}
</style>
