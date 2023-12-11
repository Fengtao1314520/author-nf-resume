<template>
  <v-card variant="flat">
    <v-row>
      <v-col cols="1" />
      <v-col>
        <v-card variant="flat">
          <v-card-title>
            <v-row class="ma-0">
              <v-icon size="middle" class="mt-2 mr-8">mdi-account-circle-outline</v-icon>
              <span>{{ localInformation.name_CN }}</span>
              <span>{{ localInformation.name_EN }}</span>
              <p class="text-body-2 text-wrap">{{ localInformation.desc }}</p>
            </v-row>
          </v-card-title>
        </v-card>
        <v-divider class="border-opacity-100" :thickness="2" />
        <v-card variant="flat">
          <v-card-title>
            <v-row class="ma-0">
              <v-icon size="middle" class="mt-2 mr-8">mdi-menu-close</v-icon>
              <span>基本信息:</span>
            </v-row>
          </v-card-title>
          <v-card-text>
            <div>
              <v-icon class="mr-8">mdi-format-title</v-icon>
              <span>{{ localInformation.title }}</span>
            </div>
            <div>
              <v-icon class="mr-8">mdi-map-marker</v-icon>
              <span>{{ localInformation.base }}</span>
            </div>
            <div>
              <v-icon class="mr-8">mdi-email-outline</v-icon>
              <span>{{ localInformation.email }}</span>
            </div>
            <div>
              <v-icon class="mr-8">mdi-github</v-icon>
              <a :href="localInformation.resume">{{ localInformation.resume }}</a>
            </div>
          </v-card-text>
        </v-card>
        <v-divider class="border-opacity-100" :thickness="2" />
        <v-card variant="flat">
          <v-card-title>
            <v-row class="ma-0">
              <v-icon size="middle" class="mt-2 mr-8">mdi-menu-close</v-icon>
              <span>教育与继续教育信息:</span>
            </v-row>
          </v-card-title>
          <v-card-text>
            <v-row class="ma-0">
              <div>
                <v-icon small class="mr-2">mdi-school-outline</v-icon>
                <span>江苏理工学院 (2022~2024)</span>
                <span class="font-italic font-weight-medium">[成考]</span>
              </div>
              <div class="ml-8">
                <v-icon small class="mr-2">mdi-school-outline</v-icon>
                <span>无锡职业技术学院 (2007~2010)</span>
              </div>
            </v-row>
          </v-card-text>
        </v-card>
        <v-divider class="border-opacity-100" :thickness="2" />
        <v-card variant="flat">
          <v-card-title>
            <v-row class="ma-0">
              <v-icon size="middle" class="mt-2 mr-8">mdi-menu-close</v-icon>
              <span>个人简介:</span>
            </v-row>
          </v-card-title>
          <v-card-text>
            <div v-for="(item, i) in localProfile" :key="i">
              <v-icon small class="mr-2">{{ item.icon }}</v-icon>
              <span>{{ item.text }}</span>
            </div>
          </v-card-text>
        </v-card>
        <v-divider class="border-opacity-100" :thickness="2" />
        <v-card variant="flat">
          <v-card-title>
            <v-row class="ma-0">
              <v-icon size="middle" class="mt-2 mr-8">mdi-menu-close</v-icon>
              <span>工作经历:</span>
            </v-row>
          </v-card-title>
          <v-card-text>
            <v-alert
              v-for="(item, i) in localExperience"
              :key="i"
              border="start"
              class="mb-2 text-black"
              color="grey-lighten-1"
              variant="outlined"
            >
              <v-icon color="black">{{ item.icon }}</v-icon>
              <span class="text-black ml-8">{{ item.text }}</span>
              <v-row class="text-black">
                <v-col>{{ item.content.datetime }}</v-col>
                <v-col>{{ item.content.company }}</v-col>
                <v-col>{{ item.content.dept }}</v-col>
              </v-row>
              <p class="text-subtitle-2 text-black">职责&业绩:</p>
              <p class="text-caption text-black" v-for="(two, k) in item.content.todo" :key="k">
                {{ two }}
              </p>
            </v-alert>
          </v-card-text>
        </v-card>
        <v-divider class="border-opacity-100" :thickness="2" />
        <v-card variant="flat">
          <v-card-title>
            <v-row class="ma-0">
              <v-icon size="middle" class="mt-2 mr-8">mdi-menu-close</v-icon>
              <span>项目经历:</span>
            </v-row>
          </v-card-title>
          <v-card-text>
            <v-alert
              v-for="(item, i) in localProject"
              :key="i"
              border="end"
              class="mb-2 text-black"
              color="grey-lighten-1"
              variant="outlined"
            >
              <v-icon color="black">{{ item.icon }}</v-icon>
              <span class="text-black ml-8">{{ item.text }}</span>
              <v-row class="text-black">
                <v-col>{{ item.datetime }}</v-col>
                <v-col>{{ item.company }}</v-col>
                <v-col>{{ item.position }}</v-col>
              </v-row>
              <p class="text-black">{{ item.desc }}</p>
              <p class="text-subtitle-2 text-black">项目职责:</p>
              <p
                class="text-caption text-black"
                v-for="(two, k) in item.content.todo"
                :key="k + '_k'"
              >
                {{ two }}
              </p>
              <p class="text-subtitle-2 text-black">项目业绩:</p>
              <p class="text-caption text-black" v-for="(three, p) in item.content.done" :key="p">
                {{ three }}
              </p>
            </v-alert>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="1" />
    </v-row>
  </v-card>
</template>

<script setup lang="ts">
import { experience } from '@/scripts/experience'
import { profile } from '@/scripts/profile'
import { information } from '@/scripts/information'
import { project } from '@/scripts/project'
import { ref } from 'vue'

const localExperience = ref(experience)
const localProfile = ref(profile)
const localInformation = ref(information)
const localProject = ref(project)
</script>

<style scoped></style>