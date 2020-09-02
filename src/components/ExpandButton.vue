<template>
  <div id="expand-button">
    <div></div>
    <div></div>
    <div></div>
  </div>
</template>

<script>
export default {
  name: "ExpandButton",

  props: {
    
  },
};
</script>

<style scoped>
#expand-button div{
  background-color: var(--text-primary);
  height: 3px;
  width: 25px;
  margin: 5px;
}
</style>