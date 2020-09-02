<template>
  <nav class="navBar">
    <router-link to="/">
      <h3>{{title}}</h3>
    </router-link>
    <ul class="navList">
      <slot></slot>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "NavBar",
  props: {
    title: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  text-decoration: none;
  color: var(--text-primary);
}
ul {
  list-style: none;
}

h3 {
  text-transform: uppercase;
  letter-spacing: 5px;
  font-size: 22px;
}

.navBar {
  display: flex;
  justify-content: space-around;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: var(--navbar-height);
  background: var(--bg-dark);
}

.navList {
  display: flex;
  width: 30%;
  justify-content: space-around;
}

@media (max-width: 22em) {
  h3 {
    text-align: left;
    font-size: 18px;
    margin: 0 1em;
  }
  .navList {
    display: none;
  }
}
</style>