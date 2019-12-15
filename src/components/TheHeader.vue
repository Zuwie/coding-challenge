<template>
  <header>
    <nav id="nav" class="inner">
      <ul class="nav-list">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/about">About</router-link></li>
        <li><router-link to="/contact">Contact</router-link></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: "TheHeader"
};
</script>

<style scoped lang="scss">
.nav-list {
  display: flex;
  padding: 30px 20px;

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
</style>
