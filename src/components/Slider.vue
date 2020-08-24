<template>
  <div class="slidecontainer">
    <input type="range" min="1" max="500" v-bind:value="number" class="slider" id="myRange" v-on:input="changeNum"/>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "Slider",
  props: {
    number: Number,
  },
  methods:{
    changeNum(event){
      this.$emit('test', event.target.value);
    }
  }
};
</script>

<style scoped>
.slidecontainer {
  display: flex;
}
.slider{

}
</style>