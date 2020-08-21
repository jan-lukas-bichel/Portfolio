<template>
  <div class="Content" v-bind:style="{ backgroundColor: bgcolor }"></div>
</template>

<script>
export default {
  name: "Content",

  props: {
    bgcolor: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.Content {
  height: 92vh;
}
</style>