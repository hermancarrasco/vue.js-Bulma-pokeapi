<template>
  <div id="app">
    <div id="nav">
      <nav class="navbar is-dark" role="navigation" aria-label="main navigation">
        <div class="navbar-brand">
          <a class="navbar-item">
            <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
          </a>

          <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
            <span aria-hidden="true"></span>
            <span aria-hidden="true"></span>
            <span aria-hidden="true"></span>
          </a>
        </div>

        <div id="navbarBasicExample" class="navbar-menu">
          <div class="navbar-start">

              <router-link to="/" class="navbar-item is-active">Pokemones</router-link>
              <router-link to="/about" class="navbar-item">About</router-link>
          </div>
        </div>
      </nav>


    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
@import "~bulma/css/bulma.min.css";
</style>
