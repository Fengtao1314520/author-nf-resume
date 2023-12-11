<template>
  <div v-if="changesample === false">
    <main-gorgeous />
  </div>
  <div v-else>
    <main-easy />
  </div>
</template>

<script setup lang="ts">
import MainEasy from '@/components/resume/MainEasy.vue'
import MainGorgeous from '@/components/resume/MainGorgeous.vue'
import { ref, watch } from 'vue'

const props = defineProps({
  changeToSample: Boolean
})

const changesample = ref(true)

// 监听changeToSample
watch(
  () => props.changeToSample,
  (value) => {
    changesample.value = value
  },
  { immediate: true, deep: true }
)
</script>

<style scoped></style>