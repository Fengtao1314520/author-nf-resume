<template>
  <v-app>
    <v-app-bar
      density="compact"
      color="deep-purple-accent-2"
      :flat="true"
      :absolute="true"
    >
      <v-app-bar-title class="font-weight-bold">
        <v-row class="ma-0">
          <v-icon @click="changeToSampleFunc" class="mr-4">
            <v-img :cover="true" :src="localsvgicon" alt="logo" />
          </v-icon>
          <p>I'm Nate Feng(冯涛)</p>
        </v-row>
      </v-app-bar-title>
      <v-spacer/>
      <v-btn icon>
        <v-icon @click="checkToEn">mdi-tram</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <i-main :changeToSample="sampleFlag" :change-to-en="enFlag"/>
    </v-main>

  </v-app>
</template>

<script setup lang="ts">
import { ref } from "vue";
import svgicon from "../public/logo/rowarlock-high-resolution-logo-transparent.svg";
import IMain from "@/components/IMain.vue";

const localsvgicon = ref(svgicon);
const sampleFlag = ref(false);
const enFlag=ref(false)

/**
 * change 展示模式
 */
function changeToSampleFunc() {
  sampleFlag.value = !sampleFlag.value;
}

function checkToEn() {
  enFlag.value =!enFlag.value
  sampleFlag.value=true
}
</script>

<style scoped></style>
