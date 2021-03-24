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
} from "@ionic/vue";

import {
  add,
  play,
  informationCircleOutline,
  caretDownOutline,
} from "ionicons/icons";

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
  },

  setup() {
    const openCategories = () => {
      console.log("Categories opened !");
    };
    return {
      add,
      play,
      informationCircleOutline,
      caretDownOutline,
      openCategories,
    };
  },
};
</script>

<style lang="scss" scoped>
.logo {
  width: 20px;
  margin-left: 16px;
  margin-top: 3px;
}

.spotlight {
  background-image: url("/assets/images/justice_league.jpg");
  width: 100%;
  height: 70vh;
  background-position: top;
  background-size: cover;
  background-repeat: no-repeat;
  position: relative;
}

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
}

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

ion-toolbar {
  --background: linear-gradient(
    0deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(1, 1, 1, 1) 100%
  );
}

ion-content {
  --offset-top: 0px;
  position: absolute;
}
</style>
