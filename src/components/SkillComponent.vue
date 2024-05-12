<template>
  <section class="skills">
    <article class="title">
      <h1 class="titleName darkText">Skills</h1>
      <div class="decoLine"></div>
    </article>

    <article class="imgSkill">
      <ul class="imgWrap">
        <li
          class="eachSkillBg button hover-shadow"
          v-for="obj in logoImgdata"
          :key="obj.id"
          rel="hover-shadow"
        >
          <img :src="obj.src" :alt="obj.name" />
        </li>
      </ul>
    </article>

    <article class="skillText">
      <div class="decoLineBlue"></div>
      <div class="textWrap">
        <h2 class="bigText">What I can do with</h2>
        <p class="longText darkText">
          웹 표준을 준수하여 시멘틱한 마크업을 구현하고 SASS를 활용하여 유지보수
          가능한 반응형 웹 사이트를 제작합니다. React, Next.js등의 프레임 워크를
          이해하고 프로젝트에 활용할 수 있으며 MySQL, MongoDB를 사용해 데이터
          관리를 해본 경험이 있습니다.
        </p>
      </div>
    </article>
  </section>
</template>
<script>
import AOS from "aos";
import { onMounted } from "@vue/runtime-core";
export default {
  data() {
    return {
      logoImgdata: [
        { id: 1, name: "html", src: require("@/assets/img/htmlLogo.png") },
        { id: 2, name: "css", src: require("@/assets/img/cssLogo.png") },
        { id: 3, name: "js", src: require("@/assets/img/jsLogo.png") },
        { id: 4, name: "react", src: require("@/assets/img/reactLogo.png") },
        { id: 5, name: "next", src: require("@/assets/img/nextLogo.png") },
        { id: 6, name: "vue", src: require("@/assets/img/vueLogo.png") },
        {
          id: 7,
          name: "react-query",
          src: require("@/assets/img/reactquery.png"),
        },
        {
          id: 8,
          name: "typescript",
          src: require("@/assets/img/typescriptLogo.png"),
        },
        { id: 9, name: "jquery", src: require("@/assets/img/jqueryLogo.png") },
        { id: 10, name: "sass", src: require("@/assets/img/sassLogo.png") },
        { id: 11, name: "figma", src: require("@/assets/img/figmaLogo.png") },
        { id: 12, name: "mySQL", src: require("@/assets/img/MySqlLogo.png") },
        {
          id: 12,
          name: "mongoDB",
          src: require("@/assets/img/mongodbLogo.png"),
        },
        {
          id: 13,
          name: "mariaDB",
          src: require("@/assets/img/mariadb.png"),
        },
      ],
    };
  },
  setup() {
    onMounted(() => {
      AOS.init();
    });
  },
};
</script>
<style scoped lang="scss">
.skills {
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
  }
  .imgSkill {
    margin-top: 20px;
    .imgWrap {
      padding: 5%;
      display: flex;
      flex-wrap: wrap;
      justify-content: flex-start;
      align-items: center;

      .eachSkillBg {
        width: 120px;
        height: 120px;
        border-radius: 25px;
        border: 2px solid #c1a7ee;
        background: #fdfeff;
        box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 1% 0.5%;
        img {
          width: 100px;
        }
      }
    }
  }
  .skillText {
    margin-top: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    .decoLineBlue {
      width: 27px;
      height: 170px;
      background: linear-gradient(180deg, #8f94ff 0%, #9ae2ff 100%);
    }
    .textWrap {
      height: 170px;
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
      align-items: flex-start;
      margin-left: 20px;
      .bigText {
        font-family: "ONE-Mobile-POP";
        font-size: 40px;
        font-weight: 400;
        background: linear-gradient(270deg, #9ae2ff 50%, #7b81fe 100%);
        background-clip: text;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
      .longText {
        margin-top: 5px;
        font-family: "Noto Sans KR";
        font-size: 16px;
        line-height: 175%;
      }
    }
  }
}
/* 
Hover Shadow 
https://androphil.tistory.com/557
*/

@keyframes hover {
  50% {
    transform: translateY(-3px);
  }
  100% {
    transform: translateY(-6px);
  }
}

@keyframes hover-shadow {
  0% {
    transform: translateY(6px);
    opacity: 0.4;
  }

  50% {
    transform: translateY(3px);
    opacity: 1;
  }

  100% {
    transform: translateY(6px);
    opacity: 0.4;
  }
}

.hover-shadow {
  display: inline-block;
  position: relative;
  transition-duration: 1000;
  transition-property: transform;

  &:before {
    pointer-events: none;
    position: absolute;
    z-index: -1;
    content: "";
    top: 100%;
    left: 5%;
    height: 10px;
    width: 90%;
    opacity: 0;
    background: radial-gradient(
      ellipse at center,
      rgba(0, 0, 0, 0.35) 0%,
      rgba(0, 0, 0, 0) 80%
    ); /* W3C */
    transition-duration: 1000;
    transition-property: transform opacity;
  }

  &:hover {
    transform: translateY(-6px);
    animation-name: hover;
    animation-duration: 1.5s;
    animation-delay: 1000;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-direction: alternate;

    &:before {
      opacity: 0.4;
      transform: translateY(6px);
      animation-name: hover-shadow;
      animation-duration: 1.5s;
      animation-delay: 0.3s;
      animation-timing-function: linear;
      animation-iteration-count: infinite;
      animation-direction: alternate;
    }
  }
}
@media (min-width: 820px) and (max-width: 1245px) {
  .skills {
    .imgSkill {
      margin-top: 10px;
      .imgWrap {
        padding: 3%;
        .eachSkillBg {
          width: 85px;
          height: 85px;
          img {
            width: 70px;
          }
        }
      }
    }
  }
}
@media (min-width: 590px) and (max-width: 819px) {
  .skills {
    .imgSkill {
      margin-top: 10px;
      .imgWrap {
        padding: 3%;
        .eachSkillBg {
          width: 60px;
          height: 60px;
          img {
            width: 50px;
          }
        }
      }
    }
  }
}
@media (min-width: 425px) and (max-width: 589px) {
  .skills {
    .imgSkill {
      margin-top: 50px;
      .imgWrap {
        padding: 3%;
        justify-content: center;
        .eachSkillBg {
          width: 50px;
          height: 50px;
          img {
            width: 40px;
          }
        }
      }
    }
    .skillText {
      margin-top: 90px;
      .textWrap .bigText {
        font-size: 35px;
      }
    }
  }
}
@media (max-width: 424px) {
  .skills {
    .title {
      .titleName {
        font-size: 40px;
      }
      .decoLine {
        width: 150px;
      }
    }
    .imgSkill {
      margin-top: 50px;
      .imgWrap {
        padding: 3%;
        justify-content: center;
        .eachSkillBg {
          width: 50px;
          height: 50px;
          img {
            width: 38px;
          }
        }
      }
    }
    .skillText {
      margin-top: 90px;
      .textWrap .bigText {
        font-size: 28px;
        margin-bottom: 10px;
      }
    }
  }
}
</style>
