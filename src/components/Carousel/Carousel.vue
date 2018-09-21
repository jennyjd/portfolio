<template>
  <div>
    <transition-group
      tag="div"
      id="carousel"
    >
      <div
        v-for="slide in slides"
        :key="slide.id"
        v-bind:class="{ 'slide-hidden': slide.id !== currentSlideId, 'slide': true }"
      >
        <h2>{{ slide.name }}</h2>
      </div>
    </transition-group>
    <button v-on:click="prevSlide">PREV</button>
    <button v-on:click="nextSlide">NEXT</button>
    <div class="carousel-actions">
      <div
        v-for="slide in slides"
        :key="slide.id"
        v-bind:class="{ 'action-active': slide.id === currentSlideId, 'action': true }"
      >
        <img :src="slide.imageSrc" alt="About me">
        <div>{{slide.name}}</div>
      </div>
    </div>
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
          name: "About Me",
          component: "",
          imageSrc: require("../../assets/girl.svg")
        },
        {
          id: 1,
          name: "Skills",
          component: "",
          imageSrc: require("../../assets/medal.svg")
        },
        {
          id: 2,
          name: "Contact",
          component: "",
          imageSrc: require("../../assets/chat.svg")
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

.carousel-actions {
  position: absolute;
  bottom: 50px;
  width: 100%;
  display: flex;
  justify-content: center;

  .action {
    cursor: pointer;
    padding: 10px;
    margin: 0 30px;
    text-transform: uppercase;
    font-weight: 500;
    opacity: 0.8;

    & > img {
      filter: grayscale(70%);
      width: 60px;
      margin-bottom: 7px;
      transition: 0.7s;
    }

    &:hover {
      @extend .action-active;
    }
  }

  .action-active {
    opacity: 1;
    & > img {
      filter: grayscale(0%);
    }
  }
}
</style>
