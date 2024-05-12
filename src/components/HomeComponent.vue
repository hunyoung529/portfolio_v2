<template>
  <div>
    <section class="leftProfile">
      <!-- Left profile content -->
    </section>

    <section class="rightMain">
      <div class="wrapRight80">
        <nav class="navTab">
          <dl class="selectTab">
            <div
              id="about"
              class="tabs"
              :class="{ active: activeTab === 'about' }"
              @click="setActiveTab('about')"
            >
              <p class="hover">About</p>
            </div>
            <div
              id="skills"
              class="tabs"
              :class="{ active: activeTab === 'skill' }"
              @click="setActiveTab('skill')"
            >
              <p class="hover">Skill</p>
            </div>
            <div
              id="project"
              class="tabs"
              :class="{ active: activeTab === 'project' }"
              @click="setActiveTab('project')"
            >
              <p class="hover">Project</p>
            </div>
          </dl>
        </nav>
        <article class="mainContent">
          <span class="toggleBtn" @click="$emit('toggle-dark-mode')">
            <img
              v-if="!darkmode"
              src="@/assets/sun.svg"
              alt="Light Mode Icon"
            />
            <img v-else src="@/assets/moon.svg" alt="Dark Mode Icon" />
          </span>
          <div v-if="activeTab === 'about'">
            <AboutComponent />
          </div>
          <div v-if="activeTab === 'skill'">
            <SkillComponent />
          </div>
          <div v-if="activeTab === 'project'">
            <ProjectComponent />
          </div>
        </article>
      </div>
    </section>
  </div>
</template>

<script>
import AOS from "aos";
import { onMounted } from "@vue/runtime-core";
import AboutComponent from "./AboutComponent.vue";
import ProjectComponent from "./ProjectComponent.vue";
import SkillComponent from "./SkillComponent.vue";
export default {
  name: "HomeFrame",
  props: ["darkmode"],
  components: { AboutComponent, SkillComponent, ProjectComponent },
  data() {
    return {
      activeTab: "about",
    };
  },
  setup() {
    onMounted(() => {
      AOS.init();
    });
  },
  methods: {
    setActiveTab(tabId) {
      this.activeTab = tabId;
    },
  },
};
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100;200;300;400;500;600;700;800;900&display=swap");

.leftProfile {
  width: 20%;
  position: absolute;
  top: 10%;
  left: 5%;
  font-family: "Noto Sans KR";
  .wrapLeft20 {
    figure {
      margin-bottom: 35px;
      img {
        width: 200px;
        height: 200px;
        border-radius: 50%;
        background-color: rgba(193, 167, 237, 0.6);
      }
    }
    .hiText {
      .hello {
        font-size: 32px;
        font-weight: 700;
        line-height: normal;
      }
      .email {
        font-size: 18px;
        font-weight: 500;
        margin-top: 10px;
      }
    }
  }
}
.rightMain {
  width: 80%;
  position: absolute;
  top: 10%;
  right: 5%;
  .wrapRight80 {
    display: flex;
    flex-direction: row;
    .navTab {
      width: 15%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: flex-end;

      .selectTab {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: flex-end;
        height: 400px;
        .tabs {
          width: 100px;
          height: 125px;
          border-radius: 25px 0px 0px 25px;
          box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
          transition: 0.3s ease-in;
          display: flex;
          justify-content: center;
          align-items: center;
          p {
            font-size: 20px;
            color: #fff;
            transition: 0.3s ease-in;
          }
        }
      }
    }
    .mainContent {
      border-radius: 0 12px 12px 12px;
      width: 85%;
      height: 85vh;

      filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
      transition: background-color 0.3s ease-in-out;
      .toggleBtn {
        z-index: 5;
        position: absolute;
        top: 5%;
        right: 5%;
        cursor: pointer;
        display: flex;
        align-items: center;
        img {
          width: 65px;
        }
      }
    }
  }
}
</style>
