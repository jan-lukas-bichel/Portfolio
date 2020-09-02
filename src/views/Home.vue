<template>
  <div id="p5sketch">
    <div class="menu">
      <div class="button-container">
        <Expand-Button v-on:click="toggleMenu" />
      </div>
      <div class="slider-group">
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
    </div>
  </div>
</template>

<script>
import Slider from "../components/Slider";
import ExpandButton from "../components/ExpandButton";
import p5 from "p5";

export default {
  name: "Home",
  components: {
    Slider,
    ExpandButton,
  },
  data() {
    return {
      menuDomElement: null,
      trailLength: 50,
      speed: 50,
      x1Amplitude: 200,
      y1Amplitude: 400,
      x2Amplitude: 500,
      y2Amplitude: 150,
    };
  },
  methods: {
    toggleMenu() {
      this.menuDomElement.classList.toggle("slider-group-collapsed");
    },
  },

  mounted() {
    this.menuDomElement = document.querySelector(".menu");
    let contentDiv = document.getElementById("p5sketch");

    const sketch = (s) => {
      let t = 0;

      s.setup = () => {
        s.createCanvas(contentDiv.clientWidth, contentDiv.clientHeight);
        s.stroke(240, 211, 116, 140);
        s.strokeWeight(3);
      };
      s.windowResized = () => {
        s.resizeCanvas(contentDiv.clientWidth, contentDiv.clientHeight);
      };
      s.draw = () => {
        s.background(132, 165, 157);
        s.translate(s.width / 2, s.height / 2);
        for (let i = 1; i <= this.trailLength / 3; i = i + 1) {
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
    let myp5 = new p5(sketch, contentDiv);
  },
};
</script>

<style scoped>
#p5sketch {
  height: 100%;
  overflow: hidden;
}

.menu {
  position: fixed;
  display: flex;
  flex-direction: column;
  height: 100%;
  z-index: 2;
  background-color: rgba(0, 0, 0, 0.3);
  transform: translateX(0%);
  transition: transform 0.5s ease-in;
  overflow-y: scroll;
  /* Hide scrollbar for IE, Edge and Firefox */
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
}
/* Hide scrollbar for Chrome, Safari and Opera */
.menu::-webkit-scrollbar {
  display: none;
}
@media (max-width: 446px) {
  .menu {
    width: 100%;
  }
}

.button-container {
  display: flex;
  justify-content: flex-end;
  padding: 0.5em;
}

.slider-group-collapsed {
  transform: translateX(-89%);
}
</style>