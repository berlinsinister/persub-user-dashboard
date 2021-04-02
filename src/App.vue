<template>
  <Header />
  <main>
    <div class="title">User Dashboard</div>
    <div class="container">
      <Sidebar @changeVisibility="changeVisibility" />
      <UserInfo :link="link" />
    </div>
  </main>
</template>

<script>
import Header from "./components/Header.vue";
import Sidebar from "./components/Sidebar.vue";
import UserInfo from "./components/UserInfo.vue";

export default {
  name: "App",
  components: { Header, Sidebar, UserInfo },
  data() {
    return {
      link: "overview", // default value
    };
  },
  methods: {
    changeVisibility(link) {
      this.link = link;
      // console.log(this.link);
    },
  },
};
</script>

<style lang="scss">
@import "./assets/sass/vars";
@import "./assets/sass/mixins";

$width: 155rem;
$height: 88rem;

:root {
  font-size: $font-size;
}

html,
body {
  @include reset;
}

body {
  font: {
    family: $font-family;
    size: 1.4rem;
    weight: 400;
  }
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #f8f8f8;
}

main {
  display: grid;
  grid-template-columns: auto;
  grid-auto-rows: auto;
  justify-content: center;
  margin: 15rem 0 7rem 0;
  & .title {
    font-size: 2.5rem;
    font-weight: 500;
    padding-bottom: 2rem;
  }
}

.container {
  display: grid;
  grid-template-columns: auto auto;
  justify-content: center;
  align-content: center;
  width: $width;
  height: $height;
  background: white;
  border: 1px solid gainsboro;
  border-radius: 1rem;
  @include around-shadow;
}

// MEDIA
@media (max-width: 1600px) {
  .container {
    width: 135rem;
  }
}

@media (max-width: 1400px) {
  .container {
    width: 115.3rem;
  }
}

@media (max-width: 1200px) {
  .container {
    width: 92.3rem;
    // border: 1px solid blue;
  }
}

@media (max-width: 1000px) {
  .container {
    width: 76rem;
  }
}

@media (max-width: 850px) {
  .container {
    grid-template-columns: auto;
    grid-template-rows: auto auto;
    align-content: start;
    grid-gap: 2rem;
    width: 32rem;
    height: auto; // 20rem;
  }
}
</style>