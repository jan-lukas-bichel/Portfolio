<template>
  <div class="home">
    <Content bgcolor="black"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Content from '../components/Content.vue'

export default {
  name: 'Home',
  components: {
    Content,
  },
}
</script>
