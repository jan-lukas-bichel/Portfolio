<template>
  <li class="nav-bar-item">
    <router-link v-bind:to="url">{{text}}</router-link>
  </li>
</template>

<script>
export default {
  name: "NavBarItem",
  props: {
    text: String,
    url: String,
  },
};
</script>

<style scoped>
a {
  text-decoration: none;
  color: var(--text-primary);
}

.nav-bar-item {
  font-weight: 600;
  font-size: 16px;
  margin-right: 3vh;
  margin-left: 3vh;
}
</style>
