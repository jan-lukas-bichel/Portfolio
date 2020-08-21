<template>
  <nav class="navBar">
    <h3 class="logo">{{title}}</h3>
    <ul class="navList">
      <NavBarItem
        v-bind:key="navBarItem.id"
        v-for="navBarItem in navBarItems"
        v-bind:text="navBarItem.text"
        v-bind:url="navBarItem.url"
      />
    </ul>
  </nav>
</template>

<script>
import NavBarItem from "./NavBarItem.vue";

export default {
  name: "NavBar",
  components: {
    NavBarItem,
  },
  props: {
    title: String,
  },
  data() {
    return {
      navBarItems:[
        {
          id: 0,
          url: "someurl",
          text: "button1"
        },
        {
          id: 1,
          url: "someotherurl",
          text: "button2"
        },
      ]
    };  
  }
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

.logo{
  text-transform: uppercase;
  letter-spacing: 5px;
  font-size: 22px;
}
</style>