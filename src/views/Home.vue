<template>
  <Content bgcolor="black" id="p5sketch"></Content>
</template>

<script>
// @ is an alias to /src
import Content from "../components/Content.vue";
import p5 from "p5";

export default {
  name: "Home",
  components: {
    Content,
  },
  mounted() {
    console.log(document.getElementById("p5sketch"));
    this.p5Setup();
  },

  methods: {
    p5Setup() {
      const s = (sketch) => {
        sketch.setup = () => {
          sketch.createCanvas(200, 200);
          sketch.background(255, 204, 0);
          sketch.textSize(32);
          sketch.text("word", 10, 60);
        };

        sketch.draw = () => {};
      };

      // eslint-disable-next-line no-unused-vars
      let myp5 = new p5(s, document.getElementById("p5sketch"));
    },
  },
};
</script>
