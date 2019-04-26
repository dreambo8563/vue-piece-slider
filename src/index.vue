<template>
  <!-- Pieces Slider -->
  <div class="pieces-slider vue-piece-slider">
    <!-- Each slide with corresponding image -->
    <div v-for="(v, i) of list" :key="i" class="pieces-slider__slide">
      <img :ref="getImgRef(i)" class="pieces-slider__image" :src="v" alt />
    </div>
    <!-- Canvas to draw the pieces -->
    <canvas class="pieces-slider__canvas"></canvas>
    <!-- Slider buttons: prev and next -->
    <button class="pieces-slider__button pieces-slider__button--prev">
      prev
    </button>
    <button class="pieces-slider__button pieces-slider__button--next">
      next
    </button>
  </div>
</template>
<script>
import anime from "animejs/lib/anime.es.js";
// window.anime = anime
import Pieces from "./piece/index.js";
// Options for images
const imageOptions = {
  angle: 45,
  extraSpacing: { extraX: 500, extraY: 200 },
  piecesWidth: function() {
    return Pieces.random(50, 200);
  },
  ty: function() {
    return Pieces.random(-400, 400);
  }
};
export default {
  props: {
    list: {
      type: Array,
      default: () => []
    },
    value: {
      type: [String, Number],
      default: 0
    }
  },
  data() {
    return {};
  },
  methods: {
    initVar() {
      this.items = [];
      this.imagesReady = 0;
      this.piecesSlider = null;
    },
    getImgRef(i) {
      const refName = `imgRef_${i}`;
      return refName;
    },
    loadImg() {
      const slidesNum = this.list.length;
      for (let i = 0; i < slidesNum; i++) {
        // Wait for all images to load before initializing the slider and event listeners
        const slideImage = new Image();
        slideImage.onload = () => {
          if (++this.imagesReady == slidesNum) {
            // console.log(slidesNum, this.imagesReady);
            this.initSlider();
            // this.initEvents()
          }
        };
        // console.log(this.$refs);
        // Push all elements for each slide with the corresponding options
        console.log(this.$refs[this.getImgRef(i)]);
        this.items.push({
          type: "image",
          value: this.$refs[this.getImgRef(i)][0],
          options: imageOptions
        });
        slideImage.src = this.list[i];
      }
    },
    initSlider() {
      // Stop any current animation if the slider was initialized before
      if (this.piecesSlider) {
        this.piecesSlider.stop();
      }

      // Save the new Pieces instance
      this.piecesSlider = new Pieces({
        canvas: ".pieces-slider__canvas",
        items: this.items,
        x: "centerAll",
        y: "centerAll",
        piecesSpacing: 1,
        animation: {
          duration: function() {
            return Pieces.random(1000, 2000);
          },
          easing: "easeOutQuint"
        }
        // debug: true
      });
      // Show current items: image, text and number
      this.showItems();
    },
    // Show current items: image, text and number
    showItems() {
      // Show image pieces
      console.log(this.piecesSlider);
      this.piecesSlider.showPieces({
        items: this.value,
        ignore: ["tx"],
        singly: true,
        update: anim => {
          // Stop the pieces animation at 60%, and run a new indefinitely animation of `ty` for each piece
          if (anim.progress > 60) {
            const piece = anim.animatables[0].target;
            const ty = piece.ty;
            anime.remove(piece);
            anime({
              targets: piece,
              ty:
                piece.h_ty < 300
                  ? [
                      { value: ty + 10, duration: 1000 },
                      { value: ty - 10, duration: 2000 },
                      { value: ty, duration: 1000 }
                    ]
                  : [
                      { value: ty - 10, duration: 1000 },
                      { value: ty + 10, duration: 2000 },
                      { value: ty, duration: 1000 }
                    ],
              duration: 2000,
              easing: "linear",
              loop: true
            });
          }
        }
      });
    },
    hideItems() {
      this.piecesSlider.hidePieces({
        items: [this.value]
      });
    },
    prevItem() {
      this.hideItems();
      const currentIndex =
        this.value > 0 ? this.value - 1 : this.list.length - 1;
      this.$emit("input", currentIndex);
      this.showItems();
    },
    nextItem() {
      this.hideItems();
      const currentIndex =
        this.value < this.list.length - 1 ? this.value + 1 : 0;
      this.$emit("input", currentIndex);
      this.showItems();
    }
  },
  mounted() {
    this.initVar();
    this.loadImg();
  }
};
</script>
<style lang="scss">
@import "index";
</style>
