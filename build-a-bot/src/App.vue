<template>
  <header>
    <nav>
      <li class="nav-item">
        <img class="logo" src="./assets/build-a-bot-logo.png" />
        Build a Bot
      </li>
    </nav>
  </header>
  <main>
    <HomePage />
  </main>
</template>

<script>
import HomePage from "./components/HomePage.vue";

export default {
  name: "App",
  components: {
    HomePage,
  },
};
</script>

<style>
body {
  background: lightgrey;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

main {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: white;
  width: 1024px;
  min-height: 300px;
  padding: 30px;
  margin: 0 auto;
}

header {
  background-color: #999;
  width: 1084px;
  margin: 0 auto;
}
ul {
  padding: 3px;
  display: flex;
}
.nav-item {
  display: inline-block;
  padding: 5px 10px;
  font-size: 22px;
  border-right: 1px solid #bbb;
}
.logo {
  vertical-align: middle;
  height: 30px;
}
</style>
