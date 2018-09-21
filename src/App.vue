<template>
  <div id="app">
    <MainPage/>
  </div>
</template>

<script>
import MainPage from "./components/MainPage/MainPage";

export default {
  name: "app",
  components: {
    MainPage
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=IBM+Plex+Mono:300,400|Raleway:300,400,500");

$light-pink: #f39d8c;
$pink: #da6b6f;
body {
  background: #f5f0eb;
  margin: 0;
  padding: 0;
}

#app {
  font-family: "Raleway", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  max-height: 100vh;
  overflow: hidden;
}
</style>
