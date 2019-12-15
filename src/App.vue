<template>
  <div id="app">
    <div id="nav" class="inner">
      <ul class="nav-list">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/about">About</router-link></li>
        <li><router-link to="/contact">Contact</router-link></li>
      </ul>
    </div>
    <main class="content-container inner">
      <router-view />
    </main>
  </div>
</template>

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

#nav {
  padding: 30px;
}

.nav-list {
  display: flex;

  li + li {
    margin-left: 20px;
  }

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
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
