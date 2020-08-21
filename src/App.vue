<template>
  <div id="app">
    <NavBar title="My Portfolio" >
      <NavBarItem text="About" url="/about" />
      <NavBarItem text="Contact" url="/contact" />
    </NavBar>
    <router-view/>
    </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import NavBarItem from './components/NavBarItem.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    NavBarItem
  },
}
</script>

<style>
body{
  margin: 0;
  margin-top: 8vh;
}

#app {
  font-family: 'Montserrat', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f0d374;
}

a{
  text-decoration: none;
  color: #f0d374;
}

ul{
  list-style: none;
}
</style>
