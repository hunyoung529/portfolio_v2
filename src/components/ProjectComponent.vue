<template>
  <section class="project">
    <article class="title">
      <h1 class="titleName darkText">Project</h1>
      <div class="decoLine"></div>
      <div class="filterButtons">
        <button
          @click="setFilter('')"
          class="filterLang"
          :class="{
            'active-dark': isFilterActive('') && darkmode,
            'active-light': isFilterActive('') && !darkmode,
          }"
        >
          All
        </button>
        <button
          @click="setFilter('React')"
          class="filterLang"
          :class="{
            'active-dark': isFilterActive('React') && darkmode,
            'active-light': isFilterActive('React') && !darkmode,
          }"
        >
          React
        </button>
        <button
          @click="setFilter('Next.js')"
          class="filterLang"
          :class="{
            'active-dark': isFilterActive('Next.js') && darkmode,
            'active-light': isFilterActive('Next.js') && !darkmode,
          }"
        >
          Next.js
        </button>
        <button
          @click="setFilter('Vue.js')"
          class="filterLang"
          :class="{
            'active-dark': isFilterActive('Vue.js') && darkmode,
            'active-light': isFilterActive('Vue.js') && !darkmode,
          }"
        >
          Vue.js
        </button>
        <button
          @click="setFilter('JavaScript')"
          class="filterLang"
          :class="{
            'active-dark': isFilterActive('JavaScript') && darkmode,
            'active-light': isFilterActive('JavaScript') && !darkmode,
          }"
        >
          JavaScript
        </button>
      </div>
    </article>
    <article class="projectWrap">
      <dl class="wrapLR" v-for="(obj, jsonK) in filteredProjects" :key="jsonK">
        <div class="wrapMain">
          <div class="leftPic">
            <ul class="imgSlide">
              <swiper
                :modules="modules"
                :pagination="true"
                class="mySwiper slideWrap"
              >
                <swiper-slide v-for="(img, imgK) in obj.imgs" :key="imgK">
                  <img :src="getImagePath(img)" class="eachImg" />
                </swiper-slide>
              </swiper>
            </ul>

            <ul class="link">
              <a :href="obj.link[0]" class="linkBox" target="_blank">
                <span></span>
                <img
                  class="iconimg"
                  src="@/assets/img/linkImg.png"
                  alt="링크 아이콘"
                />
                <p class="iconText hover">webpage</p>
              </a>
              <a :href="obj.link[1]" class="linkBox" target="_blank">
                <span></span>
                <img
                  class="iconimg hover"
                  src="@/assets/img/githubLogoDark.svg"
                  alt="깃허브 아이콘"
                />
                <p class="iconText hover">github</p>
              </a>
            </ul>
          </div>
          <div class="rightTexts">
            <h3 class="prjTitle darkText">{{ obj.name }}</h3>
            <p class="prjDate darkText">{{ obj.date }}</p>
            <b class="guideText">Planning the road</b>
            <p class="prjPlan darkText" v-html="obj.plan"></p>
            <b class="guideText">Description</b>
            <p class="prjDesc darkText" v-html="obj.desc"></p>
            <b class="guideText">Make Language</b>
            <div class="wrapLang">
              <div class="prjLang" v-for="(lang, imgL) in obj.lang" :key="imgL">
                <p class="eachLang">{{ lang }}</p>
              </div>
            </div>
          </div>
        </div>
        <div class="decoLinePurple"></div>
      </dl>
    </article>
  </section>
</template>
<script>
import projectData from "../assets/projectData";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination } from "swiper/modules";
import "swiper/css";
import "swiper/css/pagination";
export default {
  props: ["darkmode"],
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      projectData,
      filter: "",
    };
  },
  computed: {
    filteredProjects() {
      if (this.filter) {
        return this.projectData.filter((p) => p.lang.includes(this.filter));
      }
      return this.projectData;
    },
  },
  setup() {
    return {
      modules: [Pagination],
    };
  },
  methods: {
    getImagePath(img) {
      return require(`@/assets/img/pj_img/${img}`);
    },
    setFilter(language) {
      this.filter = language;
    },
    isFilterActive(filterValue) {
      return this.filter === filterValue;
    },
  },
};
</script>
<style lang="scss">
.project {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 15%;
  left: 30%;
  transform: translate(-30%, -15%);
  padding: 5%;
  .title {
    .titleName {
      font-family: "ONE-Mobile-POP";
      font-size: 52px;
      font-weight: 400;
      line-height: normal;
    }
    .decoLine {
      width: 200px;
      height: 15px;
      background-color: rgba(167, 129, 231, 0.69);
      transform: translate(0%, -90%);
    }
    .filterButtons {
      display: flex;
      text-align: center;
      justify-content: space-between;
      align-items: center;
      margin-top: 10px;
      width: 200px;
      .filterLang {
        width: 100%;
        border-radius: 50px;
        background: #8f94ff;
        border: 0;
        color: #fff;
        padding: 7px 18px;
        margin-right: 5px;
        &:hover {
          background-color: darken(#8f94ff, 10%);
        }
      }
      .active-dark {
        background-color: white;
        color: black;
      }

      .active-light {
        background-color: black;
        color: white;
      }
    }
  }
  .projectWrap {
    width: 100%;
    height: 85%;
    overflow: hidden;
    overflow-y: scroll;
    margin-top: 5px;
    .wrapLR {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      margin-bottom: 50px;
      .wrapMain {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 5%;
        .leftPic {
          width: 50%;

          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          .imgSlide {
            margin-bottom: 10px;
            width: 100%;
            height: 440px;
            .slideWrap {
              width: 340px;
              height: 440px;
              border-radius: 10px;
              swiper-slide {
                width: 100%;
                height: 100%;
              }
            }
          }
          .link {
            display: flex;
            justify-content: center;
            align-items: center;
            .linkBox {
              position: relative;
              z-index: 1;
              width: 120px;
              height: 40px;
              background-color: #4e5197;
              display: flex;
              justify-content: space-evenly;
              align-items: center;
              cursor: pointer;
              transition: 0.3s ease-in;

              &:hover span::after {
                opacity: 1;
              }
              &:nth-child(2) {
                margin-left: 10px;
              }

              span {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                height: 100%;
              }
              span::after {
                content: "";
                background: linear-gradient(90deg, #8f94ff 45%, #9ae2ff 100%);
                opacity: 0;
                display: block;
                width: 100%;
                height: 100%;
                transition: 0.3s ease-in;
              }
              .iconimg {
                z-index: 2;
                width: 20px;
                height: 20px;
              }
              .iconText {
                z-index: 2;
                color: #fff;
                text-align: center;
                font-family: "Noto Sans KR";
                font-size: 20px;
                font-weight: 700;
              }
            }
          }
        }
        .rightTexts {
          width: 45%;
          color: #000;
          .prjTitle {
            font-family: "ONE-Mobile-POP";
            font-size: 36px;
            font-weight: 400;
            margin-bottom: 10px;
            text-align: center;
          }
          .prjDate {
            font-family: Noto Sans KR;
            font-size: 12px;
            font-weight: 700;
            margin-bottom: 35px;
            text-align: center;
          }
          .guideText {
            font-family: "ONE-Mobile-POP";
            font-size: 16px;
            font-weight: 700;
            line-height: normal;

            background: linear-gradient(270deg, #9ae2ff 50%, #7b81fe 100%);
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
          }
          .prjPlan,
          .prjDesc {
            font-family: "Noto Sans KR";
            font-size: 12px;
            font-weight: 400;
            line-height: 150%;
            margin: 15px 0;
            word-break: keep-all;
          }
          .wrapLang {
            display: flex;
            flex-wrap: wrap;
            margin-top: 15px;
            .prjLang {
              display: flex;
              text-align: center;
              justify-content: center;
              align-items: center;
              margin: 3px 0 3px 5px;
              .eachLang {
                width: 100%;
                border-radius: 50px;
                background: #8f94ff;

                color: #fff;
                font-family: "Noto Sans KR";
                font-size: 12px;
                font-style: normal;
                font-weight: 500;
                padding: 7px 18px;
              }
            }
          }
        }
      }
      .decoLinePurple {
        width: 50%;
        height: 3px;
        border-radius: 25px;
        background: rgba(167, 129, 231, 0.69);
        margin-top: 50px;
      }
    }
  }
  ::-webkit-scrollbar {
    width: 10px;
    background-color: #aaadf9;
  }
  ::-webkit-scrollbar-thumb {
    width: 4px;
    height: 30px;
    background-color: #5f50bc;
    background-clip: padding-box;
    border: 3px solid transparent;
  }
}
.eachImg {
  width: 100%;
  height: 100%;
  object-fit: fill;
}
.swiper-pagination-bullet {
  background-color: #d9d9d9;
  width: 20px;
  height: 20px;
  opacity: 0.6;
}
.swiper-pagination-bullet-active {
  background-color: #a7aaff;
  opacity: 1;
}

@media (min-width: 590px) and (max-width: 819px) {
  .project {
    .projectWrap {
      .wrapMain {
        flex-direction: column-reverse;
        .leftPic {
          width: 100% !important;
        }
        .rightTexts {
          width: 100% !important;
          margin-bottom: 30px !important;
        }
      }
    }
  }
}
@media (min-width: 425px) and (max-width: 589px) {
  .project {
    .projectWrap {
      .wrapMain {
        flex-direction: column-reverse;
        .leftPic {
          width: 100% !important;
        }
        .rightTexts {
          width: 100% !important;
          margin-bottom: 30px !important;
        }
      }
    }
  }
}
@media (max-width: 424px) {
  .project {
    .title {
      .titleName {
        font-size: 40px;
      }
      .decoLine {
        width: 150px;
      }
    }
    .projectWrap {
      .wrapMain {
        flex-direction: column-reverse;
        .leftPic {
          width: 100% !important;
        }
        .rightTexts {
          width: 80% !important;
          margin-bottom: 30px !important;
        }
      }
    }
  }
}
</style>
