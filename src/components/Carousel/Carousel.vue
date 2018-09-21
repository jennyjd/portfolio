<template>
  <div>
    <transition-group
      tag="div"
      id="carousel"
    >
      <div
        v-for="slide in slides"
        :key="slide.id"
        v-bind:class="{ 'slide-hidden': slide.id !== currentSlideId }"
        class="slide"
      >
        <h2>{{ slide.name }}</h2>
      </div>
    </transition-group>
    <button v-on:click="prevSlide">PREV</button>
    <button v-on:click="nextSlide">NEXT</button>
  </div>
</template>

<script>
export default {
  name: "Carousel",
  data() {
    return {
      slides: [
        {
          id: 0,
          name: "Slide1"
        },
        {
          id: 1,
          name: "Slide2"
        },
        {
          id: 2,
          name: "Slide3"
        },
        {
          id: 3,
          name: "Slide4"
        },
        {
          id: 4,
          name: "Slide5"
        }
      ],
      currentSlideId: 0,
      carouselPosition: 0
    };
  },
  methods: {
    nextSlide: function() {
      this.currentSlideId += 1;
      this.carouselPosition -= 500;
      document.getElementById("carousel").style.transform = `translateX(${
        this.carouselPosition
      }px)`;
    },
    prevSlide: function() {
      this.currentSlideId -= 1;
      this.carouselPosition += 500;
      document.getElementById("carousel").style.transform = `translateX(${
        this.carouselPosition
      }px)`;
    }
  }
};
</script>

<style scoped lang="scss">
$slide-width: 500px;

#carousel {
  width: 10000px;
  height: 400px;
  position: relative;
  top: 0;
  left: calc(50vw - 450px);
  transition: all 0.5s;
}
.slide {
  float: left;
  height: 300px;
  width: $slide-width;
  background-color: pink;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-top: 50px;
  transition: all 0.5s;

  &-hidden {
    opacity: 0.5;
  }

  &:not(.slide-hidden) {
    margin: 0 100px;
    width: 700px;
    height: 400px;
  }
}
</style>
