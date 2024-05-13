<template>
  <div>
    <section class="leftProfile"></section>

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
            <ProjectComponent :darkmode="darkmode" />
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
@media (min-width: 820px) and (max-width: 1245px) {
  .leftProfile {
    width: 100%;
    height: 20vh;
    top: 1%;
    left: 0%;
    padding: 0 2%;
    .wrapLeft20 {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      figure {
        margin-right: 35px;
        margin-bottom: 0;
      }
      .hiText {
        .hello {
          font-size: 28px;
          font-weight: 600;
        }
        .email {
          display: none;
        }
      }
    }
  }
  .rightMain {
    width: 100%;
    height: 80vh;
    top: 7.5%;
    right: 0%;
    .wrapRight80 {
      width: 100%;
      flex-direction: column;
      .navTab {
        width: 100%;
        flex-direction: row;
        justify-content: flex-end;
        .toggleBtn {
          .toggleLabel {
            transform: rotate(-90deg) translate(65px, 350px);
          }
        }
        .selectTab {
          flex-direction: row;
          height: unset;
          margin-right: 10px;
          .tabs {
            height: 75px;
            border-radius: 25px 25px 0px 0px;
          }
        }
      }
      .mainContent {
        width: 100%;
        height: 75vh;
      }
    }
  }
} //end 1240
@media (min-width: 590px) and (max-width: 819px) {
  .leftProfile {
    width: 100%;
    height: 20vh;
    top: 1%;
    left: 0%;
    padding: 0 2%;
    .wrapLeft20 {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      figure {
        margin-right: 35px;
        margin-bottom: 0;
        img {
          width: 140px;
          height: 140px;
        }
      }
      .hiText {
        .hello {
          font-size: 28px;
          font-weight: 600;
        }
        .email {
          display: none;
        }
      }
    }
  }
  .rightMain {
    width: 100%;
    height: 80vh;
    top: 7.5%;
    right: 0%;
    .wrapRight80 {
      width: 100%;
      flex-direction: column;
      .navTab {
        width: 100%;
        flex-direction: row;
        justify-content: flex-end;
        .toggleBtn {
          .toggleLabel {
            transform: rotate(-90deg) translate(-35px, -50px);
          }
        }
        .selectTab {
          flex-direction: row;
          height: unset;
          margin-right: 10px;
          .tabs {
            height: 75px;
            border-radius: 25px 25px 0px 0px;
          }
        }
      }
      .mainContent {
        width: 100%;
        height: 75vh;
      }
    }
  }
}
@media (min-width: 425px) and (max-width: 589px) {
  .leftProfile {
    width: 100%;
    height: 20vh;
    top: 1%;
    left: 0%;
    padding: 0 2%;
    .wrapLeft20 {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      figure {
        margin-right: 35px;
        margin-bottom: 0;
        img {
          width: 140px;
          height: 140px;
        }
      }
      .hiText {
        .hello {
          font-size: 28px;
          font-weight: 600;
        }
        .email {
          display: none;
        }
      }
    }
  }
  .rightMain {
    width: 100%;
    height: 80vh;
    top: 7.5%;
    right: 0%;
    .wrapRight80 {
      width: 100%;
      flex-direction: column;
      .navTab {
        margin-top: 90px;
        width: 100%;
        flex-direction: row;
        justify-content: flex-end;

        .selectTab {
          flex-direction: row;
          height: unset;
          margin-right: 10px;
          .tabs {
            height: 75px;
            border-radius: 25px 25px 0px 0px;
          }
        }
      }
      .mainContent {
        width: 100%;
        height: 95vh;
      }
    }
  }
}
@media (max-width: 424px) {
  .leftProfile {
    width: 100%;
    height: 20vh;
    top: 1%;
    left: 0%;
    padding: 0 2%;
    .wrapLeft20 {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      figure {
        margin-right: 35px;
        margin-bottom: 0;
        img {
          width: 140px;
          height: 140px;
        }
      }
      .hiText {
        .hello {
          font-size: 20px;
          font-weight: 600;
        }
        .email {
          display: none;
        }
      }
    }
  }
  .rightMain {
    width: 100%;
    height: 80vh;
    top: 7.5%;
    right: 0%;
    .wrapRight80 {
      width: 100%;
      flex-direction: column;
      .navTab {
        margin-top: 90px;
        width: 100%;
        flex-direction: row;
        justify-content: flex-end;
        .toggleBtn {
          position: absolute;
          top: 18.5%;
          right: 12%;
          z-index: 5;
          .toggleLabel {
            transform: rotate(-90deg);
          }
        }
        .selectTab {
          flex-direction: row;
          height: unset;
          margin-right: 10px;
          .tabs {
            height: 55px;
            border-radius: 25px 25px 0px 0px;
          }
          .colorTab {
            width: 140px;
            height: 75px;
          }
        }
      }
      .mainContent {
        width: 100%;
        height: 150vh;
        .toggleBtn {
          display: none;
        }
      }
    }
  }
}
</style>
