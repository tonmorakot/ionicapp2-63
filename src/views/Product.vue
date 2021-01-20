<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>สินค้า</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">สินค้า</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-row>
        <ion-col>
          <ion-list>
            <ion-item v-for="(data, index) in products" :key="index">
              <ion-text>รหัสสินค้า : {{ data.p_id }}</ion-text>
              <ion-text>ชื่อสินค้า : {{ data.p_name }}</ion-text>
              <ion-text>ราคาขายสินค้า : {{ data.p_price_sell }}</ion-text>
              <ion-text>ราคาทุนสินค้า : {{ data.p_price_cost }}</ion-text>
            </ion-item>
          </ion-list>
        </ion-col>
      </ion-row>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonRow,
  IonCol,
  IonList,
  IonText,
  IonItem,
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
} from "@ionic/vue";

import axios from "axios";

export default {
  name: "Product",
  components: {
    IonRow,
    IonCol,
    IonList,
    IonText,
    IonItem,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
  },
  data() {
    return {
      products: null,
    };
  },
  async ionViewWillEnter() {
    const res = await axios.get("http://localhost:3000/products");
    this.products = res.data;
  },
};
</script>
