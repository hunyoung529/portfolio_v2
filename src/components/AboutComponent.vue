<template>
  <section class="about">
    <article class="title">
      <h1 class="titleName darkText">About</h1>
      <div class="decoLine"></div>
    </article>

    <article class="aboutMe">
      <div class="myProfile">
        <div class="infoText">
          <div class="decoLineBlue"></div>
          <div class="textWrap darkText">
            <h2>정훈영</h2>
            <div class="detail">
              <p>1992.5.29</p>
              <p>서울시 송파구</p>
            </div>
          </div>
        </div>

        <div class="contactInfo darkText">
          <figure class="eachInfo">
            <img src="@/assets/img/email.png" />
            <figcaption>gnsdud92@naver.com</figcaption>
          </figure>
          <figure class="eachInfo">
            <img src="@/assets/img/tel.png" />
            <figcaption>+82 10-3621-5832</figcaption>
          </figure>
        </div>
      </div>
      <div class="introduce">
        <div class="decoLineBlue"></div>
        <p class="introText darkText">
          끊임없이 성장하고 발전하는 프론트엔드 개발자입니다. <br />
          코드의 퀄리티와 효율성에 항상 주의를 기울이며, 협업과 소통을 통해
          사용자에게 <br />최상의 웹 경험을 제공하는 것을 목표로 하고 있습니다.
          매일 새로운 도전을 즐기며, <br />더 나은 개발자로 거듭나기 위해
          노력하고 있습니다.
        </p>
      </div>
    </article>

    <ul class="myPages">
      <li class="page">
        <a href="https://github.com/hunyoung529" target="blank">
          <figure class="pageInfo hover">
            <img
              class="lightImg hover"
              src="@/assets/img/githubLogo.png"
              alt="깃허브 로고"
            />
            <img
              class="darkImg hover"
              src="@/assets/img/githubLogoDark.svg"
              alt="깃허브 로고"
            />
            <figcaption class="darkText hover">Github</figcaption>
          </figure>
          <p class="pageText darkText hover">
            지금까지 제작한 프로젝트의 소스를 볼 수 있는 저장소
          </p>
        </a>
      </li>
      <li class="page">
        <a href="https://purok.tistory.com/" target="blank">
          <figure class="pageInfo hover">
            <img class="hover" src="@/assets/img/blog.svg" alt="블로그 로고" />
            <figcaption class="darkText hover">Blog</figcaption>
          </figure>
          <p class="pageText darkText hover">
            공부하며 배운 정보를 기록한 블로그
          </p>
        </a>
      </li>
    </ul>
  </section>
</template>

<script>
export default {};
</script>

<style scoped lang="scss">
.about {
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

  .aboutMe {
    display: flex;
    flex-direction: column;
    margin-top: 75px;
    .decoLineBlue {
      background: linear-gradient(180deg, #4e55e7 0%, #9ae2ff 100%);
    }
    .myProfile {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      .profilePic {
        width: 225px;
        height: 240px;
        border-radius: 48px;
        border: 3px solid #c1a7ed;
        overflow: hidden;
        img {
          width: 100%;
          height: 100%;
          object-fit: contain;
          transform: scale(1.3) translate(-2%, 10%);
        }
      }
      .infoText {
        display: flex;
        justify-content: center;
        align-items: center;

        .textWrap {
          display: flex;
          justify-content: center;
          align-items: flex-start;
          flex-direction: column;
          margin-left: 20px;
          text-align: left;
          font-weight: 400;
          line-height: normal;
          h2 {
            font-family: "ONE-Mobile-POP";
            font-size: 60px;
            font-weight: normal;
            margin-bottom: 10px;
          }
          .detail {
            margin-top: 10px;
            p {
              font-family: "Noto Sans KR";
              font-size: 16px;
            }
          }
        }
        .decoLineBlue {
          width: 27px;
          height: 170px;
        }
      }
      .contactInfo {
        display: flex;
        justify-content: center;
        align-items: flex-start;
        flex-direction: column;
        margin-left: 50px;

        .eachInfo {
          display: flex;
          justify-content: center;
          align-items: center;
          margin: 5px 0 5px 50px;

          img {
            width: 37px;
            height: 37px;
          }
          figcaption {
            font-family: "Noto Sans KR";
            font-size: 16px;
            margin-left: 5px;
          }
        }
      }
    }
    .introduce {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      margin-top: 75px;
      .decoLineBlue {
        width: 27px;
        height: 125px;
      }
      .introText {
        width: 75%;
        margin-left: 20px;

        font-family: "Noto Sans KR";
        font-size: 16px;
        font-weight: 400;
        line-height: normal;
        word-break: keep-all;
      }
    }
  }

  .myPages {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-top: 75px;
    .page {
      &:nth-of-type(2) {
        margin-left: 100px;
      }
      .pageInfo {
        display: flex;
        justify-content: flex-start;
        align-items: flex-end;
        margin-bottom: 15px;
        img {
          width: 47px;
          height: 47px;
        }
        .lightImg {
          display: block;
        }
        .darkImg {
          display: none;
        }
        figcaption {
          text-align: center;
          font-family: "ONE-Mobile-POP";
          font-size: 32px;
          margin-left: 5px;
        }
      }
      .pageText {
        font-family: "Noto Sans KR";
        font-size: 16px;
        line-height: 155%;
        word-break: keep-all;
      }
    }
  }
}
@media (min-width: 820px) and (max-width: 1245px) {
  .about {
    .aboutMe {
      margin-top: 50px;
      .introduce {
        margin-top: 50px;
      }
    }
    .myPages {
      margin-top: 50px;
    }
  }
}
@media (min-width: 590px) and (max-width: 819px) {
  .about {
    .aboutMe {
      margin-top: 40px;
      .introduce {
        margin-top: 50px;
      }
      .myProfile {
        .infoText {
          .textWrap {
            h2 {
              font-size: 52px;
            }
          }
        }
        .contactInfo {
          margin-left: -10px;
        }
      }
    }
    .myPages {
      margin-top: 50px;
    }
  }
}
@media (min-width: 425px) and (max-width: 589px) {
  .about {
    .aboutMe {
      margin-top: 40px;
      .introduce {
        margin-top: 50px;
      }
      .myProfile {
        flex-direction: column;
        align-items: flex-start;
        .contactInfo {
          margin-left: -10px;
        }
      }
      .decoLineBlue {
        height: 190px !important;
      }
    }
    .myPages {
      margin-top: 50px;
      .page:nth-of-type(2) {
        margin-left: 10px;
      }
    }
  }
}
@media (max-width: 424px) {
  .about {
    .title {
      .titleName {
        font-size: 40px;
      }
      .decoLine {
        width: 150px;
      }
    }
    .aboutMe {
      margin-top: 40px;
      .introduce {
        margin-top: 50px;
      }
      .myProfile {
        flex-direction: column;
        align-items: flex-start;
        .contactInfo {
          margin-left: -10px;
        }
      }
      .decoLineBlue {
        height: 190px !important;
      }
    }
    .myPages {
      margin-top: 50px;
      align-items: flex-start;
      .page:nth-of-type(2) {
        margin-left: 10px;
      }
      .page {
        .pageText {
          word-break: unset;
        }
        .pageInfo {
          figcaption {
            font-size: 28px;
          }
        }
      }
    }
  }
}
</style>
