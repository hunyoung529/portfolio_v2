<template>
  <div :class="{ 'dark-mode': darkmode }" class="allBg">
    <div class="allWrap">
      <HomeComponent :darkmode="darkmode" @toggle-dark-mode="modeChange" />
    </div>
  </div>
</template>

<script>
import HomeComponent from "./components/HomeComponent.vue";

export default {
  name: "App",
  components: {
    HomeComponent,
  },
  data() {
    return {
      darkmode: false,
    };
  },
  methods: {
    modeChange() {
      this.darkmode = !this.darkmode;
    },
  },
  mounted() {
    this.darkmode =
      window.matchMedia &&
      window.matchMedia("(prefers-color-scheme: dark)").matches;
  },
};
</script>

<style lang="scss">
@import "_reset";
#app {
  width: 100%;
  height: 100vh;
}

.allBg {
  transition: background-color 0.3s ease-in-out;
  background-color: #f4f5ff;
  .allWrap {
    background-image: url("@/assets/img/bgPattern.png");
    background-size: cover;
    filter: opacity(0.85);
    width: 100%;
    height: 100vh;
    position: relative;
  }
}
.mainContent {
  background-color: rgb(255, 255, 255, 0.8);
}
.tabs {
  background-color: grey;
}
.tabs.active {
  background-color: #2d2e30;
}
.dark-mode {
  background-color: #0f172a;
  .hello,
  .email {
    color: #fff;
  }
  .mainContent {
    background-color: #1e293b;
  }
  .darkText {
    color: #fff;
  }
  .decoLine {
    background: linear-gradient(180deg, #4e5197 0%, #6a74db 100%) 0.8;
  }
  .decoLineBlue {
    background: linear-gradient(180deg, #8f94ff 0%, #9ae2ff 100%);
  }
  .tabs {
    background-color: #3f5477;
  }
  .tabs.active {
    background-color: #16335c;
  }
  .lightImg {
    display: none;
  }
  .darkImg {
    display: block;
  }
}
</style>
