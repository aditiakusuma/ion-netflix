<template>
  <ion-page>
    <ion-header class="ion-no-border">
      <ion-toolbar>
        <ion-img class="logo" src="/assets/images/netflix.png"></ion-img>
        <ion-row class="ion-justify-content-center ion-text-center">
          <ion-col size="4" class="ion-text-right">
            TV Shows
          </ion-col>
          <ion-col size="4">
            Movies
          </ion-col>
          <ion-col size="4" class="ion-text-left" @click="openCategories">
            Categories
            <ion-icon :icon="caretDownOutline"></ion-icon>
          </ion-col>
        </ion-row>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <div class="spotlight">
        <div class="gradient"></div>

        <div class="info">
          <span class="rating">#1 in The World</span>

          <ion-row class="ion-align-items-center">
            <ion-col size="4" class="ion-text-center">
              <div class="btn-vertical">
                <ion-icon :icon="add"></ion-icon>
                <span>My List</span>
              </div>
            </ion-col>
            <ion-col size="4" class="ion-text-center">
              <div class="btn-play">
                <ion-icon :icon="play" color="dark"></ion-icon>
                <span>Play</span>
              </div>
            </ion-col>
            <ion-col size="4" class="ion-text-center">
              <div class="btn-vertical">
                <ion-icon :icon="informationCircleOutline"></ion-icon>
                <span>Info</span>
              </div>
            </ion-col>
          </ion-row>
        </div>
      </div>

      <div v-for="(section, index) in sections" :key="index">
        <span class="section-title">{{ section.title }}</span>
        <ion-slides :options="opts">
          <ion-slide v-for="(series, index) in section.series" :key="index">
            <img
              src="/assets/images/justice_league.jpg"
              alt=""
              v-if="section.type != 'continue'"
            />
            <div class="continue" v-if="section.type == 'continue'">
              <img src="/assets/images/justice_league.jpg" alt="" />
              <div class="progress-bar">
                <div
                  class="progress"
                  :style="`width: ${series.progress}%`"
                ></div>
              </div>
              <ion-row>
                <ion-col size="6" class="ion-text-left ion-no-padding">
                  <ion-button color="medium" size="small" fill="clear">
                    <ion-icon
                      slot="icon-only"
                      :icon="informationCircleOutline"
                    ></ion-icon>
                  </ion-button>
                </ion-col>
                <ion-col size="6" class="ion-text-right ion-no-padding">
                  <ion-button color="medium" size="small" fill="clear">
                    <ion-icon
                      slot="icon-only"
                      :icon="ellipsisVertical"
                    ></ion-icon>
                  </ion-button>
                </ion-col>
              </ion-row>
            </div>
          </ion-slide>
        </ion-slides>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonContent,
  IonRow,
  IonCol,
  IonIcon,
  IonImg,
  IonSlides,
  IonSlide,
  IonButton,
} from "@ionic/vue";

import {
  add,
  play,
  informationCircleOutline,
  caretDownOutline,
  ellipsisVertical,
} from "ionicons/icons";
import { ref } from "vue";

export default {
  name: "Tab1",
  components: {
    IonHeader,
    IonToolbar,
    IonContent,
    IonPage,
    IonRow,
    IonCol,
    IonIcon,
    IonImg,
    IonSlides,
    IonSlide,
    IonButton,
  },

  setup() {
    const openCategories = () => {
      console.log("Categories opened !");
    };

    const opts = {
      slidePerview: 2.4,
      spaceBetween: 10,
      freeMode: true,
    };

    const sections = [
      {
        title: "Continue Watching",
        type: "continue",
        series: [
          {
            id: 1,
            progress: 40,
            title: "series 1",
            season: "S1:E1",
          },
          {
            id: 1,
            progress: 40,
            title: "series 1",
            season: "S1:E1",
          },
        ],
      },
      {
        title: "Netflix Originals",
        type: "original",
        series: [
          {
            id: 1,
            progress: 40,
            title: "series 1",
            season: "S1:E1",
          },
          {
            id: 1,
            progress: 40,
            title: "series 1",
            season: "S1:E1",
          },
        ],
      },
      {
        title: "Trending Now",
        type: "trending",
        series: [
          {
            id: 1,
            progress: 40,
            title: "series 1",
            season: "S1:E1",
          },
          {
            id: 1,
            progress: 40,
            title: "series 1",
            season: "S1:E1",
          },
        ],
      },
    ];

    return {
      add,
      play,
      informationCircleOutline,
      caretDownOutline,
      openCategories,
      sections,
      ellipsisVertical,
      opts,
    };
  },
};
</script>

<style lang="scss" scoped>
ion-toolbar {
  --background: linear-gradient(
    0deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(1, 1, 1, 1) 100%
  );

  .logo {
    width: 20px;
    margin-left: 16px;
    margin-top: 3px;
  }
}

ion-content {
  --offset-top: 0px;
  position: absolute;

  .section-title {
    font-weight: 600;
    font-size: large;
  }

  ion-slides {
    margin-top: 4px;

    .continue {
      background: #191919;

      .progress-bar {
        height: 2px;
        width: 100%;
        background: #262626;

        .progress {
          background: red;
          height: 100%;
        }
      }
    }
  }

  .spotlight {
    background-image: url("/assets/images/justice_league.jpg");
    width: 100%;
    height: 70vh;
    background-position: top;
    background-size: cover;
    background-repeat: no-repeat;
    position: relative;

    .gradient {
      background: linear-gradient(#ffffff00 40%, #000000c2, #000 95%);
      width: 100%;
      height: 100%;
    }

    .info {
      position: absolute;
      width: 100%;
      bottom: 10px;
      text-align: center;

      .rating {
        display: block;
        font-weight: 700;
        padding-top: 10px;
        padding-bottom: 10px;
      }

      .btn-vertical {
        font-weight: 500;
        display: flex;
        flex-direction: column;
        align-items: center;
      }

      .btn-play {
        background: #fff;
        font-weight: 500;
        border-radius: 2px;
        color: #000;
        padding: 4px;

        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
      }
    }
  }
}
</style>
