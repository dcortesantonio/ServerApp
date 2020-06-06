<template>
  <div id="app">
      <b-navbar toggleable="md"  type="dark" variant="dark">
      <b-container>
        <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
        <b-navbar-brand href="#">Server Application |</b-navbar-brand>
        <b-collapse is-nav id="nav-collapse">
            <b-nav-item :to="{name: 'Home'}" exact><span class="text-light"><i class="fa fa-fw fa-home"></i>Home</span></b-nav-item>
            <b-nav-item :to="{name: 'History'}"><span class="text-light"><i class="fa fa-history"></i> History of Searches</span></b-nav-item>
            <b-nav-item :to="{name: 'Search'}"><span class="text-light"><i class="fa fa-fw fa-search"></i>Search</span></b-nav-item>
        </b-collapse>
      </b-container>
    </b-navbar>
      <router-view/>
  </div>


</template>

<style>

    body{
        padding-top: 20px;
        padding-bottom: 20px;
    }
 /*
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  #nav {
    padding: 30px;
  }

  #nav a {
    font-weight: bold;
    color: #2c3e50;
  }

  #nav a.router-link-exact-active {
    color: #42b983;
  }*/
</style>
