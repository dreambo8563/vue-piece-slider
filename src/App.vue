<template>
  <div class="content" id="app">
    <div class="toolbox">
      <div>
        <label for="extraX">ExtraX</label>
        <input
          type="range"
          v-model.number="options.extraSpacing.extraX"
          name="extraX"
          :min="-500"
          :max="500"
        />
        <span class="range-slider__value">{{
          options.extraSpacing.extraX
        }}</span>
      </div>
      <div>
        <label for="extraY">ExtraY</label>
        <input
          type="range"
          v-model.number="options.extraSpacing.extraY"
          name="extraY"
          :min="-500"
          :max="500"
        />
        <span class="range-slider__value">{{
          options.extraSpacing.extraY
        }}</span>
      </div>
      <div>
        <label for="angle">Angle</label>
        <input
          type="range"
          v-model.number="options.angle"
          name="angle"
          :min="0"
          :max="360"
        />
        <span class="range-slider__value">{{ options.angle }}</span>
      </div>
      <div>
        <label for="piecesWidth">PiecesWidth</label>
        <input
          type="range"
          v-model.number="options.piecesWidth"
          name="piecesWidth"
          :min="0"
          :max="200"
        />
        <span class="range-slider__value">{{ options.piecesWidth }}</span>
      </div>
      <div>
        <label for="ty">Ty (startY)</label>
        <input
          type="range"
          v-model.number="options.ty"
          name="ty"
          :min="-300"
          :max="300"
        />
        <span class="range-slider__value">{{ options.ty }}</span>
      </div>
      <div>
        <label for="piecesSpacing">PiecesSpacing</label>
        <input
          type="range"
          v-model.number="options.piecesSpacing"
          name="piecesSpacing"
          :min="0"
          :max="100"
        />
        <span class="range-slider__value">{{ options.piecesSpacing }}</span>
      </div>
    </div>
    <Slider
      :arrow="true"
      :options="options"
      @click="click"
      class="slider"
      :list="list"
      v-model="activeIndex"
    ></Slider>
  </div>
</template>

<script>
import Slider from "./index.vue";

export default {
  name: "app",
  data() {
    return {
      activeIndex: 0,
      list: [
        "./img/1.jpg",
        "./img/2.jpg",
        "./img/3.jpg",
        "./img/4.jpg",
        "./img/5.jpg"
      ],
      options: {
        angle: 30,
        extraSpacing: { extraX: 1, extraY: -20 },
        piecesWidth: 100,
        ty: 200,
        piecesSpacing: 1,
        animation: {
          duration: 2000,
          easing: "easeOutQuint"
        }
      }
    };
  },
  components: {
    Slider
  },
  methods: {
    click() {
      // eslint-disable-next-line no-console
      console.info("object");
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  .slider {
    width: 400px;
    height: 200px;
  }
  .toolbox {
    margin-right: 100px;
    display: flex;
    flex-direction: column;
    & > div {
      margin: 20px;
      label {
        margin-right: 10px;
        font-weight: bold;
        color: white;
        font-size: 1em;
        padding: 0.75em;
      }
      input {
        vertical-align: middle;
      }
      .range-slider__value {
        display: inline-block;
        position: relative;
        width: 60px;
        color: #fff;
        line-height: 20px;
        text-align: center;
        border-radius: 3px;
        background: #2c3e50;
        padding: 5px 10px;
        margin-left: 8px;

        &:after {
          position: absolute;
          top: 50%;
          left: -6px;
          width: 0;
          transform: translateY(-50%);
          height: 0;
          font-weight: bold;
          border-top: 6px solid transparent;
          border-right: 6px solid #2c3e50;
          border-bottom: 6px solid transparent;
          content: "";
        }
      }
    }
  }
}
</style>
