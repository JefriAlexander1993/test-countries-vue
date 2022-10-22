<!--<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>

-->

<template>
  <div>
    <header-bar></header-bar>
    <b-container>
      <b-row class="mt-5">
        <router-view />
      </b-row>
    </b-container>
  </div>
</template>

<script>
import HeaderBar from "@/components/HeaderBar.vue";

export default {
  components: {
    HeaderBar,
  },
};
</script>
