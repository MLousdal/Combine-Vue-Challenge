<template>
  <Header></Header>
  <header class="title">
    <h1>Besøgsoplevelse</h1>
    <p>Hvordan var din kundeoplevelse i butikken i dag?</p>
  </header>
  <Main></Main>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Lobster&family=Source+Sans+Pro:wght@400;600&display=swap");

body {
  font-family: Source Sans Pro;
  font-style: normal;
  font-weight: 600;
  font-size: 16px;
  line-height: 20px;
}

.wrapper {
  max-width: 1240px;
  margin: 0 auto;
  width: 95%;
}

.title {
  margin-top: 2rem;

  h1 {
    color: #149d2a;
    font-size: 56px;
    font-style: normal;
    font-weight: bold;
    line-height: 70px;
    text-align: center;
  }

  p {
    font-size: 22px;
    line-height: 28px;
    text-align: center;
  }
}
</style>
