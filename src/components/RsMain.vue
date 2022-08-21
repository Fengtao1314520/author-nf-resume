<template>
  <v-container>
    <v-card elevation="0">
      <v-row class="pa-0">
        <v-col cols="3" class="px-0">
          <v-card elevation="0">
            <p class="text-h3 text--darken-4 purple--text" @click="changeToSample">
              <span>{{ proinfo.name_CN }}</span>
              <span class="text-h6 font-italic"> {{ proinfo.name_EN }} </span>
            </p>
            <p>{{ proinfo.title }}</p>
            <v-card elevation="0" class="mt-4">
              <p class="text-h5 text--darken-4 purple--text">联系方式</p>
              <v-text-field
                :value="proinfo.email"
                prepend-icon="mdi-email-outline"
                dense
                readonly
              ></v-text-field>
              <v-text-field
                :value="proinfo.resume"
                prepend-icon="mdi-github"
                dense
                readonly
              ></v-text-field>
              <v-text-field
                :value="proinfo.base"
                prepend-icon="mdi-map-marker"
                dense
                readonly
              ></v-text-field>
            </v-card>
            <v-card elevation="0" class="mt-4">
              <p class="text-h5 text--darken-4 purple--text">个人技能</p>
              <v-chip
                v-for="(item, i) in proskill"
                :key="i"
                small
                class="ma-1"
                color="indigo darken-1"
                label
                text-color="white"
              >
                {{ item }}
              </v-chip>
            </v-card>
            <v-card elevation="0" class="mt-4">
              <p class="text-h5 text--darken-4 purple--text">编程&框架</p>
              <v-chip
                v-for="(item, i) in softskill"
                :key="i"
                small
                class="ma-1"
                color="indigo darken-1"
                label
                text-color="white"
              >
                {{ item }}
              </v-chip>
            </v-card>
            <v-card elevation="0" class="mt-4">
              <p class="text-h5 text--darken-4 purple--text">关键词</p>
              <v-row v-for="(item, i) in keywords" :key="i">
                <v-col cols="5" class="py-1">
                  <v-chip
                    class="px-2 text-left"
                    x-small
                    color="grey darken-1"
                    label
                    text-color="white"
                  >
                    {{ item.name }}
                  </v-chip>
                </v-col>
                <v-col class="py-1">
                  <v-progress-linear
                    height="10"
                    class="mt-2"
                    :value="item.value"
                    color="green accent-4"
                    rounded
                  />
                </v-col>
              </v-row>
            </v-card>
            <v-card elevation="0" class="mt-4">
              <p class="text-h5 text--darken-4 purple--text">教育&语言</p>
              <v-text-field
                value="无锡职业技术学院"
                prepend-icon="mdi-school-outline"
                dense
                disabled
              ></v-text-field>
              <v-row>
                <v-col cols="5" class="py-1">
                  <v-chip
                    x-small
                    color="grey darken-1"
                    label
                    text-color="white"
                  >
                    英语
                  </v-chip>
                </v-col>
                <v-col class="py-1">
                  <v-progress-linear
                    height="10"
                    class="mt-2"
                    value="50"
                    color="green accent-4"
                    rounded
                  />
                </v-col>
              </v-row>
            </v-card>
            <v-card elevation="0" class="mt-4">
              <p class="text-h5 text--darken-4 purple--text">继续教育</p>
              <v-text-field
                value="江苏理工学院"
                prepend-icon="mdi-school-outline"
                dense
                disabled
              ></v-text-field>
            </v-card>
            <v-card elevation="0" class="mt-4">
              <p class="text-h5 text--darken-4 purple--text">RoWarlock的思想</p>
              <p class="text-caption">
                RoWarlock从无到有，皆受HP的影响，从最初的模仿到最终的独立发展
              </p>
              <v-list flat disabled>
                <v-list-item-group color="primary">
                  <v-list-item
                    v-for="(item, i) in rowarlock"
                    :key="i"
                    dense
                    class="px-0"
                  >
                    <v-list-item-icon class="mr-1 ml-0">
                      <v-icon
                        v-text="item.icon"
                        small
                        color="green accent-4"
                      ></v-icon>
                    </v-list-item-icon>
                    <p class="text-overline mb-0">
                      {{ item.text }}
                    </p>
                  </v-list-item>
                </v-list-item-group>
              </v-list>
            </v-card>
          </v-card>
        </v-col>
        <v-col class="px-0">
          <v-card elevation="0">
            <v-card-title class="py-0">
              <p class="text-h5 text--darken-4 purple--text">个人简介</p>
            </v-card-title>
            <v-card-text class="pb-0">
              <v-alert
                border="left"
                colored-border
                color="deep-purple accent-4"
                elevation="0"
                dense
              >
                <v-list disabled dense>
                  <v-list-item-group color="primary">
                    <v-list-item v-for="(item, i) in profile" :key="i" dense>
                      <v-list-item-icon class="mr-4">
                        <v-icon v-text="item.icon" color="pink lighten-1" />
                      </v-list-item-icon>
                      <p class="my-2 text-caption">{{ item.text }}</p>
                    </v-list-item>
                  </v-list-item-group>
                </v-list>
              </v-alert>
            </v-card-text>
          </v-card>
          <v-card elevation="0">
            <v-card-title class="py-0">
              <p class="text-h5 text--darken-4 purple--text">工作经历</p>
            </v-card-title>
            <v-card-text class="pb-0">
              <v-alert
                border="left"
                colored-border
                color="green accent-4"
                elevation="0"
                dense
              >
                <v-list dense disabled>
                  <v-list-item v-for="(item, i) in experience" :key="i" dense>
                    <v-card elevation="0" class="pl-2">
                      <v-row class="my-0">
                        <v-icon class="mr-5" v-text="item.icon" />
                        <p class="text-h6 mt-n1 my-0">{{ item.text }}</p>
                      </v-row>
                      <v-row class="my-1 ml-2">
                        <v-row class="ma-1">
                          <p class="mr-4">
                            <span class="font-weight-black font-italic pr-3"
                              >公司:</span
                            >
                            <span>{{ item.content.company }}</span>
                          </p>
                          <p class="mr-4">
                            <span class="font-weight-black font-italic pr-3"
                              >部门:</span
                            >
                            <span>{{ item.content.dept }}</span>
                          </p>
                          <p>
                            <span class="font-weight-black font-italic pr-3"
                              >时间:</span
                            >
                            <span>{{ item.content.datetime }}</span>
                          </p>
                        </v-row>

                        <v-row class="mt-0">
                          <v-col class="py-1">
                            <p class="font-weight-black font-italic">简介:</p>
                            <p class="text-caption">{{ item.content.desc }}</p>
                          </v-col>
                        </v-row>
                        <v-row class="mt-0">
                          <v-col class="py-1">
                            <p class="font-weight-black font-italic">
                              工作内容:
                            </p>
                            <p
                              class="text-body-2"
                              v-for="(one, j) in item.content.todo"
                              :key="j"
                            >
                              {{ one }}
                            </p>
                          </v-col>
                        </v-row>
                      </v-row>
                    </v-card>
                  </v-list-item>
                </v-list>
              </v-alert>
            </v-card-text>
          </v-card>
          <v-card elevation="0">
            <v-card-title class="py-0">
              <p class="text-h5 text--darken-4 purple--text">项目经历</p>
            </v-card-title>
            <v-card-text class="pb-0">
              <v-alert
                border="left"
                colored-border
                color="indigo accent-4"
                elevation="0"
                dense
              >
                <v-list dense disabled>
                  <v-list-item v-for="(item, i) in projects" :key="i" dense>
                    <v-card elevation="0" class="pl-2 py-2">
                      <v-row class="my-0">
                        <v-icon v-text="item.icon" class="mr-4" />
                        <p class="text-h6 mt-n1 my-0">{{ item.text }}</p>
                      </v-row>
                      <v-row class="my-0">
                          <v-btn
                            x-small
                            v-for="(one, j) in item.content.tech"
                            :key="j"
                            depressed
                            disabled
                            class="mr-2 mt-2"
                          >
                            {{ one }}
                          </v-btn>
                      </v-row>
                      <v-row class="my-0">
                        <p class="font-weight-black font-italic mt-4 mb-0">
                          项目职责:
                        </p>
                      </v-row>
                      <v-row class="mt-0">
                        <v-col>
                          <p
                            class="text-body-2 mb-2"
                            v-for="(two, k) in item.content.todo"
                            :key="k"
                          >
                            {{ two }}
                          </p>
                        </v-col>
                      </v-row>
                    </v-card>
                  </v-list-item>
                </v-list>
              </v-alert>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'RsMain',
  data() {
    return {
      // 个人信息
      proinfo: {
        name_CN: '冯涛',
        name_EN: 'Nate Ford',
        title: '全栈&测试开发工程师(SDET)',
        tel: '17701503218',
        email: 'fengtao.1314520@163.com',
        resume: 'fengtao1314520.github.io/resume',
        base: '常州',
      },
      // 个人技能
      proskill: [
        'SCRUM',
        'TDD/BDD',
        'SVN',
        'GIT',
        'Visual Studio/Code',
        'WebStorm',
        'Node.js',
        '.NET Core',
      ],
      // 编程与框架
      softskill: [
        '.Net C#',
        'JavaScript',
        'Type Script',
        'VUE.js',
        'Selenium',
        'playwright',
        'WinAppDriver',
        'Cucumber',
        'Appium',
        'Calabash',
        'cypress',
        'Python',
        'XML/XSD',
      ],
      // 关键词
      keywords: [
        {
          name: '.NET C#',
          value: 70,
        },
        {
          name: 'JS/TS',
          value: 60,
        },
        {
          name: 'VUE.JS',
          value: 50,
        },
        {
          name: 'WEB自动化',
          value: 80,
        },
        {
          name: 'APP自动化',
          value: 60,
        },
        {
          name: '桌面自动化',
          value: 50,
        },
        {
          name: '框架开发',
          value: 70,
        },
      ],
      // 个人简介
      profile: [
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '独立开发RoWarlock自动化测试工具&管理系统',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '具有针对web、桌面程序、APP独立进行全新&二次开发完整工具&框架的经验',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '能够基于Vue.js框架，使用JS/TS语言独立自行开发web前端; 能够基于NancyFX/EmbedIO,使用.NET C#语言独立开发Web后端',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '熟悉和擅长使用多种开源、闭源商用性自动化测试工具',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '具有全新&二次完整编写手动Case与Case框架、体系的经验',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '熟悉和擅长设计、撰写、执行测试用例; 具有改进现有测试Case、框架的能力',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '具有一定的测试团队管理能力, 可以独立组织测试团队进行测试',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '熟悉和了解TDD/BDD、Scrum体系',
        },
      ],
      // 工作经历
      experience: [
        {
          icon: 'mdi-map-marker-circle',
          text: '全栈测试工程师',
          content: {
            company: '梅特勒·托利多',
            dept: '商衡事业部(RTPO)',
            datetime: '2017-02~至今',
            desc: 'PC上位机包含Web版和桌面端以及云端，旨在PC端对嵌入式秤、PC秤进行数据管理，秤管理、各类自动化执行以及数据回传保存和生成报表以及复杂操作',
            todo: [
              '1.作为全栈测试工程师，进行PC端自动化测试工具的开发、测试和使用;',
              '2.编写和测试自动化测试脚本;基于PC上位机软件进行自动化测试工作;',
              '3.基于PC上位机软件进行手动测试, 管理和执行测试用例;',
              '4.开发和编写手动测试Case;',
              '5.针对不同区域客户进行远程技术支持，包含售前，售后服务等',
              '6.对PC团队内测试人员进行日常管理, 包括任务分拆，指派和跟踪;日常工作进度提醒;',
            ],
          },
        },
        {
          icon: 'mdi-map-marker-circle',
          text: '自动化测试工程师',
          content: {
            company: '常州赞奇科技',
            dept: '测试部',
            datetime: '2015-08~2017-02',
            desc: '专业云平台，提供私有、公有云渲染服务,包含集群、客户端、web端控制台等软件',
            todo: [
              '1.作为自动化测试工程师，提供UI自动化测试工具的开发、测试和使用;',
              '2.提供性能测试的工具开发、测试和使用;',
            ],
          },
        },
        {
          icon: 'mdi-map-marker-circle',
          text: '测试主管、自动化测试开发工程师',
          content: {
            company: '文思海辉',
            dept: '游戏基地、展讯、HP',
            datetime: '2011-02~2015-08',
            desc: '国内最大的离岸服务外包公司; 游戏基地为江苏移动的移动端手机游戏APP商城; 展讯为展讯芯片兼容与APP测试; HP为HP scan自动化工具开发和自动化测试',
            todo: [
              '1.作为测试主管，负责与管理游戏基地的测试工作，包含测试用例的编写、测试用例的执行、测试用例的维护、测试用例的统计、测试用例的检查、测试用例的报表生成等;',
              '2.作为测试主管，负责管理游戏机基地内部的职能管理，包含人员招聘、面试；日程管理，任务分发等;',
              '3.作为测试主管, 负责部门与学校的校企合作;',
              '4.作为自动化测试开发工程师, 负责独立开发HP scan APP的自动化测试工具，并指导美国、印度团队进行脚本开发;',
              '5.作为自动化测试开发工程师, 协同开发HP Print PC软件的自动化测试工;',
            ],
          },
        },
      ],
      // 项目经历
      projects: [
        {
          icon: 'mdi-card-bulleted-outline',
          text: 'RoWarlock (PRO)',
          content: {
            tech: [
              'VUE.JS',
              'VUETIFY.JS',
              'JavaScript',
              'TypeScript',
              '.NET C#',
              'Playwright',
              'Postman',
            ],
            todo: [
              '1.独立开发完整的自动化测试工具&软件, 包含完整的自动化测试工具的开发、测试和使用;',
              '2.包含接口测试、Web UI自动化测试',
              '3.包含释放管理, 包含测试执行、结果回收和实时展示',
              '4.使用VUE.JS+VUETIFY.JS开发完整的Web前端的各个功能',
              '5.使用.NET C#开发完整的服务后端的各个功能',
              '6.使用TS开发完整的脚本执行器和脚本管理器',
              '7.使用Playwright开发完整的Web浏览器的各个功能',
              '8.根据Postman开发完整的API测试工具的各个功能'
            ],
          },
        },
        {
          icon: 'mdi-card-bulleted-outline',
          text: 'MT-PC上位机',
          content: {
            tech: [
              '功能测试',
              'Web UI 自动化',
              'CASE架构',
              '.NET C#',
              'Selenium',
              'XML/XSD',
              'Python',
              'TypeScript',
              'C++',
            ],
            todo: [
              '1.编写和管理手动测试PC上位机软件的case',
              '2.基于手动case编写自动化测试脚本(包含C#和XML两类脚本)',
              '3.开发web端自动化测试工具，研究手机与客户端自动化测试',
              '4.开发基于协议的新版秤内自动化测试工具,基于C#/TS重写秤内测试工具',
              '5.开发和维护旧版城内自动化测试工具，基于C++开发秤内测试工具',
            ],
          },
        },
        {
          icon: 'mdi-card-bulleted-outline',
          text: '赞奇-自动化测试',
          content: {
            tech: ['功能测试', '.NET C#', 'Selenium', 'XML/XSD'],
            todo: ['1.开发了Web自动化测试工具', '2.开发后端集群的性能测试工具'],
          },
        },
        {
          icon: 'mdi-card-bulleted-outline',
          text: '文思海辉-HP scan APP自动化测试',
          content: {
            tech: ['Powershell', '.NET C#', 'Calabash', 'Cucumber', 'Ruby'],
            todo: [
              '1.基于HP内部自动化测试工具开发PC端的测试脚本',
              '2.开发APP端scan软件的自动化测试工具和脚本, 基于Calabash(BDD)开发',
              '3.开发自动化测试执行工具',
            ],
          },
        },
      ],
      // rowarlock影响
      rowarlock: [
        {
          icon: 'mdi-atom-variant',
          text: '元素集、参数、逻辑操作三部分分离',
        },
        {
          icon: 'mdi-atom-variant',
          text: '脚本不依赖语言自身解析，脚本即是文档',
        },
        {
          icon: 'mdi-atom-variant',
          text: '工具即是大集合',
        },
        {
          icon: 'mdi-atom-variant',
          text: '编程脚本大于文本脚本',
        },
        {
          icon: 'mdi-atom-variant',
          text: 'RoWarlock 3.x coming soon',
        },
      ],
    };
  },
  methods:{
    // 更改简单模式(更加简洁)
    changeToSample(){
      this.$emit('changeToSample',true);
    }
  }
};
</script>

<style scoped></style>
