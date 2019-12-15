<template>
  <div id="app">
    <the-header></the-header>
    <main class="content-container inner">
      <router-view />
    </main>
  </div>
</template>

<script>
import TheHeader from "@/components/TheHeader";

export default {
  name: "App",
  components: {
    TheHeader
  }
};
</script>

<style lang="scss">
body,
html,
ul,
li {
  padding: 0;
  margin: 0;
}

ul {
  list-style-type: none;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.inner {
  max-width: 1400px;
  margin: 0 auto;
}

.page-title {
  text-align: center;
  text-transform: uppercase;
  margin-bottom: 3em;
}

.section-title {
  text-align: center;
  text-transform: uppercase;
  margin-bottom: 2em;
}
</style>
