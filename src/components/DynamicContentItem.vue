<template>
  <li class="nav-bar-item">
    <a v-bind:href="url">{{text}}</a>
  </li>
</template>

<script>
export default {
  name: "NavBarItem",
  props: {
      text: String,
      url: String
  },
}
</script>

<style scoped>
  .nav-bar-item {
    font-weight: 600;
    font-size: 16px;
    margin-right: 3vh;
    margin-left: 3vh;
  }
</style>
