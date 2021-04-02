<template>
  <div class="user-info-container">
    <div class="content">
      <div class="profile">
        <img src="../assets/images/profile.jpg" alt="profile" />
        <div class="status"></div>
        <div class="name-and-gender">
          <div class="name">Beka Kvartskhava</div>
          <div class="gender">Male</div>
        </div>
      </div>
      <Overview v-show="visibility.overview" />
      <div v-show="visibility.transactions" class="other-page">
        Transactions
      </div>
      <div v-show="visibility.address" class="other-page">Address</div>
      <div v-show="visibility.payment" class="other-page">Payment Methods</div>
      <Settings v-show="visibility.settings" />
    </div>
  </div>
</template>

<script>
import Settings from "./Settings.vue";
import Overview from "./Overview.vue";

export default {
  name: "UserInfo",
  components: { Overview, Settings },
  props: {
    link: String,
  },
  data() {
    return {
      visibility: {
        overview: true, // default setting
        transactions: false,
        address: false,
        payment: false,
        settings: false,
      },
    };
  },
  methods: {},
  watch: {
    // like updated() hook, but only for the 'link' prop on update
    link(newVal, oldVal) {
      // console.log("Prop changed: ", newVal, " | was: ", oldVal);
      this.visibility[oldVal] = false;
      this.visibility[newVal] = true;
    },
  },
};
</script>

<style lang="scss">
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

$user-info-width: 112rem;
$user-info-height: 73rem;

// $other-page-width: 100rem;
// $other-page-height: 50rem;

.other-page {
  display: grid;
  border: 1px solid gainsboro;
}

.user-info-container {
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: auto auto;
  justify-content: center;
  align-content: start;
  width: $user-info-width;
  height: $user-info-height;
  //   border: 1px solid red;
  & .content {
    $reduce: 6rem;
    width: $user-info-width - $reduce * 2;
    // height: $user-info-height - $reduce; // auto;
    // border: 1px solid green;
    display: grid;
    grid-template-columns: auto;
    grid-template-rows: auto auto;
    // justify-content: start;
    align-content: start;
    grid-gap: 7rem;
    & .profile {
      display: grid;
      grid-template-columns: auto auto;
      grid-template-rows: auto;
      grid-gap: 4rem;
      justify-content: start;
      position: relative;
      // border: 1px solid green;
      $img-width: 14rem;
      $status-width: 2rem;
      & img {
        // $img-width: 14rem;
        width: $img-width;
        height: $img-width;
        border-radius: 50%;
        object-fit: cover;
        border: 2px solid white;
        box-shadow: 0 5px 10px -1px rgba(black, 0.2);
      }
      & .status {
        position: absolute;
        width: $status-width;
        height: $status-width;
        top: $img-width - $status-width - 1rem;
        left: $img-width - $status-width - 1rem;
        border-radius: 50%;
        background: #74c299;
        border: 2px solid white;
      }
      & .name-and-gender {
        display: grid;
        align-content: center;
        grid-gap: 0.5rem;
        & .name {
          font-weight: 500;
          font-size: 2.4rem;
        }
        & .gender {
          color: gray;
        }
      }
    }
  }
}

// MEDIA
@media (max-width: 1600px) {
  $reduce: 6rem;
  $user-info-width: 100rem;

  .user-info-container {
    width: $user-info-width;
    // border: 1px solid crimson;
    & .content {
      width: $user-info-width - $reduce * 2;
      //   border: 1px solid green;
    }
  }
}

@media (max-width: 1400px) {
  $reduce: 6rem;
  $user-info-width: 80.3rem;

  .user-info-container {
    width: $user-info-width;
    & .content {
      width: $user-info-width - $reduce * 2;
    }
  }
}

@media (max-width: 1200px) {
  $reduce: 6rem;
  $user-info-width: 65.3rem;

  .user-info-container {
    width: $user-info-width;
    & .content {
      width: $user-info-width - $reduce * 2;
    }
  }
}

@media (max-width: 1000px) {
  $reduce: 6rem;
  $user-info-width: 51rem;

  .user-info-container {
    width: $user-info-width;
    & .content {
      width: $user-info-width - $reduce * 2;
      grid-gap: 3rem;
    }
  }
}

@media (max-width: 850px) {
  $user-info-width: 32rem;
  .user-info-container {
    width: $user-info-width;
    & .content {
      width: $user-info-width - 4rem;
      //   border: 1px solid blue;
      & .profile {
        grid-gap: 2rem;
        $img-width: 9rem;
        $status-width: 1.5rem;
        & img {
          width: $img-width;
          height: $img-width;
        }
        & .status {
          width: $status-width;
          height: $status-width;
          top: $img-width - $status-width - 0.5rem;
          left: $img-width - $status-width - 0.5rem;
        }
        & .name-and-gender {
          & .name {
            // font-weight: 500;
            font-size: 2rem;
          }
        }
      }
    }
  }
}
</style>