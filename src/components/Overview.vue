<template>
  <div class="overview-container">
    <div
      class="logo-name-and-number"
      v-for="(detail, index) in overviewDetails"
      :key="index"
    >
      <div class="logo" :style="{ background: detail.background }">
        <i :class="detail.fa"></i>
      </div>
      <div class="name-and-number">
        <div class="name">{{ detail.name }}</div>
        <div class="number">
          {{ detail.number }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Overview",
  data() {
    return {
      overviewDetails: [
        {
          background: "#64a8e3",
          fa: "fas fa-shopping-cart",
          name: "Food Delivered",
          number: "26.450",
        },
        {
          background: "#58b7a6",
          fa: "fas fa-star",
          name: "Satisfaction Rating",
          number: "95%",
        },
        {
          background: "#f6c15d",
          fa: "fas fa-wallet",
          name: "Your Balance",
          number: "IDR 2.560.800",
        },
      ],
    };
  },
  methods: {},
};
</script>

<style lang="scss">
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

$overview-width: 100rem;

.overview-container {
  display: grid;
  grid-template-columns: repeat(3, auto);
  grid-template-rows: auto;
  align-content: start;
  grid-gap: 3rem;
  width: $overview-width;
  & .logo-name-and-number {
    display: grid;
    grid-template-columns: auto auto;
    grid-template-rows: auto;
    grid-gap: 3rem;
    justify-content: start;
    & .logo {
      $size: 6.5rem;
      width: $size;
      height: $size;
      border-radius: 35%;
      display: flex;
      justify-content: center;
      align-items: center;
      & .fas {
        color: white;
        font-size: 2.5rem;
      }
    }
    & .name-and-number {
      display: grid;
      align-content: center;
      & .name {
        font-weight: 500;
        font-size: 1.4rem;
        color: gray;
      }
      & .number {
        font-weight: 600;
        font-size: 3rem;
        color: #112539;
      }
    }
  }
}

// MEDIA
@media (max-width: 1600px) {
  .overview-container {
    width: 88rem;
  }
}

@media (max-width: 1400px) {
  .overview-container {
    grid-template-columns: auto auto;
    width: 68.3rem;
  }
}

@media (max-width: 1200px) {
  .overview-container {
    grid-template-columns: auto;
    grid-gap: 2rem;
    width: 53.3rem;
  }
}

@media (max-width: 850px) {
  $overview-width: 32rem;
  .overview-container {
    width: $overview-width - 4rem;
    & .logo-name-and-number {
      grid-gap: 2rem;
      & .logo {
        $size: 5rem;
        width: $size;
        height: $size;
        & .fas {
          font-size: 2rem;
        }
      }
      & .name-and-number {
        & .number {
          font-size: 2.5rem;
        }
      }
    }
  }
}
</style>