<template>
  <div class="settings-container">
    <div class="settings-details">
      <input type="text" name="" id="name" value="Beka" />
      <input type="text" name="" id="surname" value="Tutashkhia" />
      <input type="text" name="" id="email" value="mail@gmail.com" />
      <input type="text" name="" id="tel" value="+995 559 99 00 99" />
      <input type="text" name="" id="birthday" value="1991.04.24" />
      <input type="text" name="" id="location" value="Tbilisi, Georgia" />
      <input type="password" name="" id="pass-1" value="password" />
      <input type="password" name="" id="pass-2" value="password" />
    </div>
    <div class="save-button">
      <input type="submit" value="Save" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Settings",
  data() {
    return {};
  },
  methods: {},
};
</script>

<style lang="scss">
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

$settings-width: 100rem; // 112rem;
// $settings-height: 73rem;

.settings-container {
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: auto auto;
  //   justify-content: center;
  align-content: start;
  width: $settings-width;
  grid-gap: 3rem;
  //   border: 1px solid royalblue;
  grid-template-areas: "inputs" "button";
  & .settings-details {
    display: grid;
    grid-template-columns: auto auto;
    grid-template-rows: repeat(4, auto);
    grid-gap: 3rem;
    & input {
      height: 7rem;
      padding: 0 2rem;
      color: gray;
      border-radius: 1rem;
      border: 1px solid gainsboro;
      font-size: 1.6rem;
      &:focus {
        outline: none;
      }
    }
  }
  & .save-button {
    grid-area: button;
    justify-self: end;
    & input[type="submit"] {
      width: 28rem;
      height: 5rem;
      border: none;
      border-radius: 1rem;
      background: linear-gradient(0deg, #56bd99, #9cdf77);
      color: white;
      font-size: 1.6rem;
      font-weight: 600;
      transition: $transition-time ease-out;
      &:focus {
        outline: none;
      }
      &:hover {
        cursor: pointer;
        background: linear-gradient(180deg, #56bd99, #9cdf77);
      }
    }
  }
}

// MEDIA
@media (max-width: 1600px) {
  $settings-width: 88rem;
  .settings-container {
    width: $settings-width;
  }
}

@media (max-width: 1400px) {
  $settings-width: 68.3rem;
  .settings-container {
    width: $settings-width;
  }
}

@media (max-width: 1200px) {
  $settings-width: 53.3rem;
  .settings-container {
    width: $settings-width;
    & .save-button {
      justify-self: center;
    }
  }
}

@media (max-width: 1000px) {
  $settings-width: 39rem;
  .settings-container {
    width: $settings-width;
    grid-gap: 2rem;
    & .settings-details {
      grid-template-columns: auto;
      grid-template-rows: repeat(8, auto);
      grid-gap: 1rem;
      & input {
        height: 4rem;
        padding: 0 1rem;
        font-size: 1.4rem;
      }
    }
    & .save-button {
      & input[type="submit"] {
        width: 20rem;
        height: 4rem;
        font-size: 1.4rem;
        font-weight: 500;
      }
    }
  }
}

@media (max-width: 850px) {
  $settings-width: 32rem;
  .settings-container {
    width: $settings-width - 4rem;
    & .save-button {
      & input[type="submit"] {
        width: $settings-width - 4rem;
      }
    }
  }
}
</style>