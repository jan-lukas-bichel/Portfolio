<template>
  <div class="Content" v-bind:style="{ backgroundColor: bgcolor }">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "Content",

  props: {
    bgcolor: String,
  },
};
</script>

<style scoped>
.Content {
  height: 92vh;
}
</style>