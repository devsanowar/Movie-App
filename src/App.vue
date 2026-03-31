<script setup></script>

<template>
  <header>
    <router-link :to="{ name: 'home' }">
      <h2 class="logo">Movie <span>App</span></h2>
    </router-link>
  </header>

  <main>
    <router-view> </router-view>
  </main>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;

  &::selection {
    background: transparentize($color: #34d999, $amount: 0.5);
  }
}

body {
  background-color: #454545;
}

a {
  text-decoration: none;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color:#1e293b;
  padding: 10px 20px;
  box-shadow: 0px 0px 6px rgba($color: #000000, $alpha: 0.1);
  h2 {
    color: #fff;
    font-size: 28px;

    span {
      color: #34d999;
    }
  }
}
</style>
