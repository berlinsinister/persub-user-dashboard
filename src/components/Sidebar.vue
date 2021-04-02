<template>
  <div v-show="windowWidth > 850" class="sidebar-container">
    <div
      v-for="(link, index) in sidebarLinks"
      :key="index"
      class="sidebar-link"
      :class="currentLink === index ? 'active-link' : 'passive-link'"
      @click="clickHandler(link, index)"
    >
      {{ link }}
    </div>
  </div>
  <!-- ** screen 850px and less-->
  <div v-show="windowWidth <= 850" class="sidebar-container">
    <div
      v-for="(link, index) in sidebarIcons"
      :key="index"
      :title="link.name"
      class="sidebar-link"
      :class="currentLink === index ? 'active-link' : 'passive-link'"
      @click="clickHandler(link.name, index)"
    >
      <i :class="link.fa"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  data() {
    return {
      windowWidth: window.innerWidth,
      currentLink: 0,
      sidebarLinks: [
        "Overview",
        "Transactions",
        "Address",
        "Payment Methods",
        "Settings",
      ],
      sidebarIcons: [
        { fa: "fas fa-user", name: "Overview" },
        { fa: "fas fa-coins", name: "Transactions" },
        { fa: "fas fa-map-marker-alt", name: "Address" },
        { fa: "fas fa-credit-card", name: "Payment Methods" },
        { fa: "fas fa-cog", name: "Settings" },
      ],
    };
  },
  mounted() {
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    });
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      this.windowWidth = window.innerWidth;
    },
    clickHandler(link, index) {
      this.currentLink = index;
      link = link === "Payment Methods" ? "payment" : link.toLowerCase();
      // console.log(link);
      this.$emit("changeVisibility", link);
    },
  },
};
</script>

<style lang="scss">
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

$sidebar-width: 28rem;
$sidebar-height: 73rem;

.active-link {
  color: $gray;
  transform: translate(5px);
  &::after {
    content: "\0020\203A\203A";
  }
}

.passive-link {
  color: gainsboro;
}

.sidebar-container {
  display: grid;
  grid-template-columns: auto;
  grid-auto-rows: auto;
  justify-content: start;
  align-content: start;
  grid-gap: 6rem;
  width: $sidebar-width;
  height: $sidebar-height;
  font-size: 1.8rem;
  font-weight: 500;
  border-right: 1px solid gainsboro;
  & .sidebar-link {
    transition: $transition-time ease-out;
    &:hover {
      cursor: pointer;
      color: $gray;
      transform: translate(5px);
    }
  }
}

// MEDIA
@media (max-width: 1600px) {
  $sidebar-width: 20rem;
  .sidebar-container {
    width: $sidebar-width;
  }
}

@media (max-width: 1200px) {
  $sidebar-width: 17rem;
  .sidebar-container {
    width: $sidebar-width;
    grid-gap: 3rem;
    font-size: 1.6rem;
  }
}

@media (max-width: 850px) {
  .active-link {
    transform: none;
    &::after {
      content: "";
    }
  }

  .passive-link {
    color: white;
  }

  $sidebar-width: 32rem;
  .sidebar-container {
    grid-template-columns: repeat(5, auto);
    grid-template-rows: auto;
    justify-content: center; // start;
    align-content: center; // start;
    grid-gap: 2.5rem;
    width: $sidebar-width;
    height: 9rem;
    background: linear-gradient(180deg, #56bd99, #9cdf77);
    font-size: 3rem;
    font-weight: 500;
    border-top-left-radius: 1rem;
    border-top-right-radius: 1rem;
    border-right: none;
    border-bottom: 1px dashed gainsboro;
    & .sidebar-link {
      &:hover {
        transform: none;
      }
    }
  }
}
</style>