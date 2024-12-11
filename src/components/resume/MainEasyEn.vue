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
              <span>Basic Information:</span>
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
              <span>Education and Continuing Education Information:</span>
            </v-row>
          </v-card-title>
          <v-card-text>
            <v-row class="ma-0">
              <div v-for="(item, i) in localEducation" :key="i" class="mr-8">
                <v-icon small class="mr-2">{{item.icon}}</v-icon>
                <span>{{item.school}}({{item.start}}~{{item.end}})</span>
                <span class="font-italic font-weight-medium">[{{item.degree}}]</span>
              </div>
            </v-row>
          </v-card-text>
        </v-card>
        <v-divider class="border-opacity-100" :thickness="2" />
        <v-card variant="flat">
          <v-card-title>
            <v-row class="ma-0">
              <v-icon size="middle" class="mt-2 mr-8">mdi-menu-close</v-icon>
              <span>Personal Profile:</span>
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
              <span>Work Timeline:</span>
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
              <p class="text-subtitle-2 text-black">Duty:</p>
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
              <span>Project Timeline:</span>
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
              <p class="text-subtitle-2 text-black">Duty:</p>
              <p
                  class="text-caption text-black"
                  v-for="(two, k) in item.content.todo"
                  :key="k + '_k'"
              >
                {{ two }}
              </p>
              <p class="text-subtitle-2 text-black">Performance:</p>
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
import { experience } from '@/scripts/en/experience'
import { profile } from '@/scripts/en/profile'
import { information } from '@/scripts/en/information'
import { project } from '@/scripts/en/project'
import {education} from "@/scripts/en/education";
import { ref } from 'vue'

const localExperience = ref(experience)
const localProfile = ref(profile)
const localInformation = ref(information)
const localProject = ref(project)
const localEducation = ref(education)
</script>

<style scoped></style>