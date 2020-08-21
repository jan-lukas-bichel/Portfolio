<template>
  <nav class="navBar">
    <h3 class="title">{{title}}</h3>
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
.navBar {
  display: flex;
  justify-content: space-around;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 96%;
  min-height: 8vh;
  padding-left: 2%;
  padding-right: 2%;
  background: #555;
}

.navList{
  display: flex;
  width: 30%;
  justify-content: space-around;
}

.title{
  text-transform: uppercase;
  letter-spacing: 5px;
  font-size: 22px;
}
</style>