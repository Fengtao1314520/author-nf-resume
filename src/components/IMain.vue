<template>
  <div v-if="changeEn===true">
    <div v-if="changeSample === false">
      <main-gorgeous />
    </div>
    <div v-else>
      <main-easy />
    </div>
  </div>
  <div v-else>
    <main-easy-en/>
  </div>
</template>

<script setup lang="ts">
import MainEasy from '@/components/resume/MainEasy.vue'
import MainGorgeous from '@/components/resume/MainGorgeous.vue'
import { ref, watch } from 'vue'
import MainEasyEn from "@/components/resume/MainEasyEn.vue";

const props = defineProps({
  changeToSample: Boolean,
  changeToEn: Boolean
})

const changeSample = ref(true)
const changeEn = ref(false)

// 监听changeToSample
watch(
  () => props.changeToSample,
  (value) => {
    changeSample.value = value
  },
  { immediate: true, deep: true }
)

// 监听changeToEn
watch(
  () => props.changeToEn,
  (value) => {
    changeEn.value=value
  },
  { immediate: true, deep: true }
)
</script>

<style scoped></style>