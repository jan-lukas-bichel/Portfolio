<template>
  <Content bgcolor="black" id="p5sketch">
    <div class="sliderContainer">
      <Slider v-bind:number="x1Amplitude" v-on:test="this.x1Amplitude = Number($event)">
        <p>X1 Amplitude</p>
      </Slider>
      <Slider v-bind:number="y1Amplitude" v-on:test="this.y1Amplitude = Number($event)">
        <p>Y1 Amplitude</p>
      </Slider>
      <Slider v-bind:number="x2Amplitude" v-on:test="this.x2Amplitude = Number($event)">
        <p>X2 Amplitude</p>
      </Slider>
      <Slider v-bind:number="y2Amplitude" v-on:test="this.y2Amplitude = Number($event)">
        <p>Y2 Amplitude</p>
      </Slider>
      <Slider v-bind:number="trailLength" v-on:test="this.trailLength = Number($event)">
        <p>Trail Length</p>
      </Slider>
      <Slider v-bind:number="speed" v-on:test="this.speed = Number($event)">
        <p>Speed</p>
      </Slider>
    </div>
  </Content>
</template>

<script>
import Slider from "../components/Slider";
import Content from "../components/Content";
import p5 from "p5";

export default {
  name: "Home",
  components: {
    Slider,
    Content,
  },
  data() {
    return {
      trailLength: 9,
      speed: 100,
      x1Amplitude: 20,
      y1Amplitude: 40,
      x2Amplitude: 150,
      y2Amplitude: 150,
    };
  },
  methods: {
    changeNum(event, varToChange) {
      console.log(varToChange);
      varToChange = Number(event);
    },
  },

  mounted() {
    let contentDiv = document.getElementById("p5sketch");

    const sketch = (s) => {
      let t = 0;

      s.setup = () => {
        s.createCanvas(contentDiv.clientWidth, contentDiv.clientHeight);
        s.stroke(255, 131, 15, 120);
        s.strokeWeight(5);
      };
      s.windowResized = () => {
        s.resizeCanvas(contentDiv.clientWidth, contentDiv.clientHeight);
      };
      s.draw = () => {
        s.background(57, 64, 83);
        s.translate(s.width / 2, s.height / 2);
        for (let i = 1; i <= (this.trailLength / 3); i = i + 1) {
          s.line(s.x1(t + i), s.y1(t + i), s.x2(t + i), s.y2(t + i));
        }
        t += this.speed / 500;
      };

      s.x1 = (t) => {
        return s.cos(t / 20) * this.x1Amplitude;
      };
      s.y1 = (t) => {
        return s.sin(t / 10) * this.y1Amplitude + s.sin(t / 5) * 50;
      };
      s.x2 = (t) => {
        return s.cos(t / 10) * this.x2Amplitude + s.cos(t / 15) * 75;
      };
      s.y2 = (t) => {
        return s.sin(t / 20) * this.y2Amplitude;
      };
    };

    // eslint-disable-next-line no-unused-vars
    let myp5 = new p5(sketch, document.getElementById("p5sketch"));
  },
};
</script>

<style scoped>
#p5Sketch {
}
.sliderContainer{
  display: flex;
  justify-content: space-evenly;
}
</style>