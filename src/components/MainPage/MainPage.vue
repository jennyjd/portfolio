<template>
  <div class="mainPage">
    <Carousel />
  </div>
</template>

<script>
import Carousel from "../Carousel/Carousel";

export default {
  name: "MainPage",
  components: {
    Carousel
  }
};
</script>

<style scoped lang="scss">
.mainPage {
  margin-top: 60px;
}

.name {
  text-transform: uppercase;
  letter-spacing: 3px;
  font-size: 1.4em;
}

.position {
  letter-spacing: 1px;
  font-family: "IBM Plex Mono";
  font-weight: 300;
  padding: 5px 0 20px;
  font-size: 0.9em;
}

.about {
  background-color: white;
  padding: 50px;
  width: 50vw;
  margin: auto;
  border-radius: 3px;
}

.myPhoto {
  border-radius: 50%;
  width: 150px;
  height: 150px;
  object-fit: cover;
  transition: filter 0.7s;

  &:hover {
    // -webkit-filter: grayscale(100%); /* Safari 6.0 - 9.0 */
    // filter: grayscale(100%);
    -webkit-filter: blur(1px); /* Safari 6.0 - 9.0 */
    filter: blur(1px) grayscale(100%);
  }
}
</style>
