<template>
  <ion-content fullscreen>
    <ion-row>
      <ion-col
        size="12"
        v-for="(category, index) in categories"
        :key="index"
        class="ion-text-center"
      >
        {{ category }}
      </ion-col>
    </ion-row>
  </ion-content>
  <ion-footer class="ion-text-center">
    <ion-toolbar>
      <ion-button @click="closeModal" fill="clear" color="light">
        <ion-icon slot="icon-only" :icon="closeCircle"></ion-icon>
      </ion-button>
    </ion-toolbar>
  </ion-footer>
</template>

<script lang="ts">
import {
  IonContent,
  IonRow,
  IonCol,
  IonFooter,
  IonButton,
  IonIcon,
  IonToolbar,
} from "@ionic/vue";
import { closeCircle } from "ionicons/icons";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Modal",
  components: {
    IonContent,
    IonRow,
    IonCol,
    IonFooter,
    IonButton,
    IonIcon,
    IonToolbar,
  },
  props: {
    categories: { type: Array },
    closeModal: { type: Function },
  },
  setup() {
    const content = "Content";

    return { content, closeCircle };
  },
});
</script>

<style lang="scss" scoped>
ion-content {
  --background: transparent;

  ion-row {
    margin-top: 10vh;

    ion-col {
      margin-bottom: 30px;
      color: var(--ion-color-medium);
    }
  }
}

ion-toolbar {
  --background: transparent;
  --border-style: none;
  height: max-content;

  ion-button {
    height: max-content;
    ion-icon {
      font-size: 50px;
    }
  }
}
</style>
