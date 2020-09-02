<template>
  <NavBar title="p5.js Experiment">
    <NavBarItem text="About" url="/about" />
    <NavBarItem text="Contact" url="/contact" />
  </NavBar>
  <router-view />
</template>

<script>
import NavBar from "./components/NavBar.vue";
import NavBarItem from "./components/NavBarItem.vue";

export default {
  name: "App",
  components: {
    NavBar,
    NavBarItem,
  },
};
</script>

<style>
#app {
  font-family: "Montserrat", sans-serif;
  
  --text-primary: #f0d374;
  --bg-dark: #545e75;
  --bg-light: #84a59d;
  --navbar-height: 75px;
  
  margin-top: var(--navbar-height);
  height: calc(100vh - var(--navbar-height));
  scrollbar-color: var(--bg-dark) var(--bg-light);
  background-color: var(--bg-light);
  color: var(--text-primary);
}

html,
body {
  margin: 0;
  overflow-x: hidden;
}
</style>
