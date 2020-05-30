<template>
  <div id="app">
    <main id="main" role="main">
      <nav-bar />
      <nuxt />
    </main>
  </div>
</template>

<script>
import NavBar from "~/components/NavBar";
export default {
  components: {
    NavBar
  }
};
</script>

<style lang="scss">
@import "../assets/scss/styles.scss";
</style>
