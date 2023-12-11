<template>
  <v-card variant="flat">
    <v-row>
      <v-col cols="1" />
      <v-col>
        <v-row class="ma-0">
          <v-col cols="3">
            <v-card variant="flat">
              <p class="text-h4 text-purple-darken-4">
                <span>{{ localInformation.name_CN }}</span>
                <span class="text-body-1 font-italic"> {{ localInformation.name_EN }} </span>
              </p>
              <p class="text-body-2">{{ localInformation.title }}</p>
              <v-card elevation="0" class="my-2">
                <p class="text-h6 text--darken-4 text-purple-darken-4">基本信息</p>
                <v-text-field
                  :value="localInformation.email"
                  prepend-icon="mdi-email-outline"
                  density="compact"
                  variant="underlined"
                  :readonly="true"
                ></v-text-field>
                <v-textarea
                  :value="localInformation.resume"
                  prepend-icon="mdi-github"
                  density="compact"
                  variant="underlined"
                  :readonly="true"
                  rows="2"
                ></v-textarea>
                <v-text-field
                  :value="localInformation.base"
                  prepend-icon="mdi-map-marker"
                  density="compact"
                  variant="underlined"
                  :readonly="true"
                ></v-text-field>
              </v-card>
              <v-card variant="flat" class="my-2">
                <p class="text-h6 text--darken-4 text-purple-darken-4">个人技能</p>
                <v-chip
                  v-for="(item, i) in personalSkill"
                  :key="i"
                  small
                  density="compact"
                  class="ma-1 font-weight-bold text-caption"
                  color="indigo-accent-4"
                  variant="flat"
                  :label="true"
                >
                  {{ item }}
                </v-chip>
              </v-card>
              <v-card variant="flat" class="my-2">
                <p class="text-h6 text--darken-4 text-purple-darken-4">编程&框架</p>
                <v-chip
                  v-for="(item, i) in softwareSkill"
                  :key="i"
                  small
                  density="compact"
                  class="ma-1 font-weight-bold text-caption"
                  color="indigo-accent-4"
                  variant="flat"
                  :label="true"
                >
                  {{ item }}
                </v-chip>
              </v-card>
              <v-card variant="flat" class="my-2">
                <p class="text-h6 text--darken-4 text-purple-darken-4">关键词</p>
                <v-row v-for="(item, i) in keyWords" :key="i" class="ma-0">
                  <v-col cols="4" class="py-0 px-0">
                    <v-chip
                      small
                      density="compact"
                      class="ma-1 font-weight-bold text-caption"
                      color="orange-accent-4"
                      variant="flat"
                      :label="true"
                    >
                      {{ item.name }}
                    </v-chip>
                  </v-col>
                  <v-col class="py-0 pl-0">
                    <v-progress-linear
                      height="10"
                      class="mt-3"
                      :model-value="item.value"
                      rounded
                      color="green-accent-4"
                    />
                  </v-col>
                </v-row>
              </v-card>
              <v-card variant="flat">
                <p class="text-h6 text--darken-4 text-purple-darken-4">教育&语言</p>
                <div>
                  <v-icon size="x-small" class="mr-2">mdi-school-outline</v-icon>
                  <span class="text-caption">江苏理工学院 (2022~2024)</span>
                  <span class="text-caption font-italic font-weight-medium">[成考]</span>
                </div>
                <div>
                  <v-icon size="x-small" class="mr-2">mdi-school-outline</v-icon>
                  <span class="text-caption">无锡职业技术学院 (2007~2010)</span>
                </div>
                <v-row class="ma-0">
                  <v-col cols="2" class="px-0 py-0">
                    <v-chip size="x-small" color="grey-lighten-1" :label="true" variant="flat">
                      英语
                    </v-chip>
                  </v-col>
                  <v-col class="py-0">
                    <v-progress-linear
                      height="10"
                      class="mt-3"
                      model-value="55"
                      color="green-accent-4"
                    />
                  </v-col>
                </v-row>
              </v-card>
            </v-card>
          </v-col>
          <v-col>
            <v-card variant="flat">
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
                    color="indigo-accent-4"
                    variant="text"
                  >
                    <v-icon color="black">{{ item.icon }}</v-icon>
                    <span class="text-black ml-8">{{ item.text }}</span>
                    <v-row class="text-black">
                      <v-col>{{ item.content.datetime }}</v-col>
                      <v-col>{{ item.content.company }}</v-col>
                      <v-col>{{ item.content.dept }}</v-col>
                    </v-row>
                    <p class="text-subtitle-2 text-black">职责&业绩:</p>
                    <p
                      class="text-caption text-black"
                      v-for="(two, k) in item.content.todo"
                      :key="k"
                    >
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
                    border="start"
                    class="mb-2 text-black"
                    color="deep-purple-accent-4"
                    variant="text"
                  >
                    <v-icon color="black">{{ item.icon }}</v-icon>
                    <span class="text-black ml-8">{{ item.text }}</span>
                    <v-row class="text-black">
                      <v-col>{{ item.datetime }}</v-col>
                      <v-col>{{ item.company }}</v-col>
                      <v-col>{{ item.position }}</v-col>
                    </v-row>
                    <p class="text-black">{{ item.desc }}</p>
                    <v-row class="ma-0 mb-1">
                      <v-btn
                        size="x-small"
                        v-for="(one, j) in item.content.tech"
                        :key="j"
                        variant="flat"
                        color="blue-accent-4"
                        class="mr-2 mt-2"
                      >
                        {{ one }}
                      </v-btn>
                    </v-row>
                    <p class="text-subtitle-2 text-black">项目职责:</p>
                    <p
                      class="text-caption text-black"
                      v-for="(two, k) in item.content.todo"
                      :key="k + '_k'"
                    >
                      {{ two }}
                    </p>
                    <p class="text-subtitle-2 text-black">项目业绩:</p>
                    <p
                      class="text-caption text-black"
                      v-for="(three, p) in item.content.done"
                      :key="p"
                    >
                      {{ three }}
                    </p>
                  </v-alert>
                </v-card-text>
              </v-card>
            </v-card>
          </v-col>
        </v-row>
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
import { keywords, personalskill, softwareskill } from '@/scripts/gorgeousLabel'
import { ref } from 'vue'

const localExperience = ref(experience)
const localProfile = ref(profile)
const localInformation = ref(information)
const localProject = ref(project)
const personalSkill = ref(personalskill)
const softwareSkill = ref(softwareskill)
const keyWords = ref(keywords)
</script>

<style scoped></style>