<template>
  <ion-page>
    <ion-tabs ref="tabs" @ionTabsDidChange="setSelectedTab()">
      <ion-tab-bar slot="bottom">
        <ion-tab-button tab="tab1" href="/tabs/tab1">
          <ion-icon :icon="selected == 'tab1' ? home : homeOutline" />
          <ion-label>Tab 1</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab2" href="/tabs/tab2">
          <ion-icon :icon="selected == 'tab2' ? copy : copyOutline" />
          <ion-label>Tab 2</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab3" href="/tabs/tab3">
          <ion-icon :icon="selected == 'tab3' ? search : searchOutline" />
          <ion-label>Tab 3</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab4" href="/tabs/tab4">
          <ion-icon :icon="selected == 'tab4' ? download : downloadOutline" />
          <ion-label>Tab 4</ion-label>
        </ion-tab-button>
      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script lang="ts">
import {
  IonTabBar,
  IonTabButton,
  IonTabs,
  IonLabel,
  IonIcon,
  IonPage,
} from "@ionic/vue";
import {
  home,
  copy,
  search,
  download,
  homeOutline,
  copyOutline,
  searchOutline,
  downloadOutline,
} from "ionicons/icons";
import { ref } from "vue";
import { useRoute } from "vue-router";

export default {
  name: "Tabs",
  components: { IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPage },
  setup() {
    const route = useRoute();
    const selected = ref<any>();

    const tabs = ref();

    const setSelectedTab = () => {
      selected.value = route.meta.tab;
    };
    return {
      home,
      copy,
      search,
      download,
      selected,
      homeOutline,
      copyOutline,
      searchOutline,
      downloadOutline,
      setSelectedTab,
      tabs,
    };
  },
};
</script>

<style lang="scss" scoped>
ion-tab-button {
  --color-selected: var(--ion-color-light);
}
</style>
