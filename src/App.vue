<template>
  <div id="app">
    <div id="nav">
    <div class="row">
    <h4 style="text-align: left; padding-left: 10px; padding-right: 25px; text-decoration: none;"><router-link to="/movies">RedBlocks</router-link></h4>
    <div class="navbar-btns">
      <router-link to="/movies" style="padding: 0px 5px;">Movies</router-link> |
      <router-link to="/about" style="padding: 0px 5px;">About</router-link> |
      <router-link to="/customers" style="padding: 0px 5px;">Customers</router-link>
      </div>
      </div>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
/* Add Google Font */
@import url('https://fonts.googleapis.com/css?family=Open+Sans:300,400,700');

/* This is where we inport our custom CSS files */
@import './assets/styles/custom.css';

#app {
  font-family: 'Open Sans', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  h5 a:hover {
    text-decoration: none;
  }
  .navbar-btns {
    margin-top: 4px;
  }

  h5 a {
    color: #2c3e50 !important;
  }
  a {
    font-family: 'Montserrat', sans-serif;

    color: white;
    &.router-link-exact-active {
      color: #7b7d82;
    }
  }
}
</style>
