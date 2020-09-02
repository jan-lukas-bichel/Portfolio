<template>
  <div class="slidecontainer">
    <slot></slot>
    <input
      type="range"
      min="1"
      max="500"
      v-bind:value="number"
      class="slider"
      id="myRange"
      v-on:input="changeNum"
    />
  </div>
</template>

<script>
export default {
  name: "Slider",
  props: {
    number: Number,
  },
  methods: {
    changeNum(event) {
      this.$emit("test", event.target.value);
    },
  },
};
</script>

<style scoped>
.slidecontainer {
  margin: 2.5em 4em;
  display: flex;
  justify-content: space-between;
}
p {
  margin: 0;
}
.slider {
  margin-left: 1.5rem;
  margin-right: 1.5rem;
}
@media (max-width: 446px) {
  .slidecontainer {
    display: block;
    margin: 2.5em 0;
  }
  .slider {
    margin:0;
  }
}
</style>