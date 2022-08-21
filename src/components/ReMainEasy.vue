<template>
  <v-container>
    <v-card flat>
      <v-card-title @click="changeToSample" class="pb-0">
        <v-app-bar color="white" dense flat>
          <v-app-bar-nav-icon>
            <v-icon>mdi-account-circle-outline</v-icon>
          </v-app-bar-nav-icon>
          <v-toolbar-title>
            <span class="mr-4"> {{ proinfo.name_CN }}</span>
            <span class="mr-4">{{ proinfo.name_EN }}</span>
          </v-toolbar-title>
        </v-app-bar>
      </v-card-title>
      <p class="ml-8 text-caption">{{ proinfo.desc }}</p>
      <v-divider />
      <v-card-text>
        <v-card flat>
          <v-app-bar color="white" dense flat>
            <v-app-bar-nav-icon disabled />
            <v-toolbar-title class="text-h6 pl-0">基本信息:</v-toolbar-title>
          </v-app-bar>
          <v-card-text class="pt-0">
            <div class="mr-8">
              <v-icon small class="mr-2">mdi-format-title</v-icon>
              <span>{{ proinfo.title }}</span>
            </div>
            <div class="mr-8">
              <v-icon small class="mr-2">mdi-map-marker</v-icon>
              <span>{{ proinfo.base }}</span>
            </div>
            <div class="mr-8">
              <v-icon small class="mr-2">mdi-email-outline</v-icon>
              <span>{{ proinfo.email }}</span>
            </div>
            <div class="mr-8">
              <v-icon small class="mr-2">mdi-github</v-icon>
              <span>{{ proinfo.resume }}</span>
            </div>
          </v-card-text>
        </v-card>
        <v-card flat>
          <v-app-bar color="white" dense flat>
            <v-app-bar-nav-icon disabled />
            <v-toolbar-title class="text-h6 pl-0"
              >教育与继续教育信息:</v-toolbar-title
            >
          </v-app-bar>
          <v-card-text class="pt-0">
            <v-row class="ma-0">
              <div class="mr-8">
                <v-icon small class="mr-2">mdi-school-outline</v-icon>
                <span>无锡职业技术学院 (2007~2010)</span>
              </div>
              <div class="mr-8">
                <v-icon small class="mr-2">mdi-school-outline</v-icon>
                <span>江苏理工学院 (2022~2024) </span>
              </div>
            </v-row>
          </v-card-text>
        </v-card>
        <!--
        <v-card flat>
          <v-app-bar color="white" dense flat>
            <v-app-bar-nav-icon disabled />
            <v-toolbar-title class="text-h6 pl-0">个人简述:</v-toolbar-title>
          </v-app-bar>
          <v-card-text class="pt-0">
            <div v-for="(item, i) in profile" :key="i">
              <v-icon small class="mr-2">{{ item.icon }}</v-icon>
              <span>{{ item.text }}</span>
            </div>
          </v-card-text>
        </v-card>
        -->
        <v-divider />
        <v-card flat>
          <v-app-bar color="white" dense flat>
            <v-app-bar-nav-icon disabled />
            <v-toolbar-title class="text-h6 pl-0">工作经历:</v-toolbar-title>
          </v-app-bar>
          <v-card-text class="pt-0">
            <v-alert
              v-for="(item, i) in experience"
              :key="i"
              border="left"
              color="grey lighten-5"
              class="black--text"
              dark
            >
              <v-icon color="black">{{ item.icon }}</v-icon>
              {{ item.text }}
              <v-row class="my-2">
                <v-col>{{ item.content.datetime }}</v-col>
                <v-col>{{ item.content.company }}</v-col>
                <v-col>{{ item.content.dept }}</v-col>
              </v-row>
              <p class="text-subtitle-2">职责&业绩:</p>
              <p
                class="text-caption mb-2"
                v-for="(two, k) in item.content.todo"
                :key="k"
              >
                {{ two }}
              </p>
            </v-alert>
          </v-card-text>
        </v-card>
        <v-divider />
        <v-card flat>
          <v-app-bar color="white" dense flat>
            <v-app-bar-nav-icon disabled />
            <v-toolbar-title class="text-h6 pl-0">项目经历:</v-toolbar-title>
          </v-app-bar>
          <v-card-text class="pt-0">
            <v-alert
              v-for="(item, i) in projects"
              :key="i"
              border="right"
              color="grey lighten-5"
              class="black--text"
              dark
            >
              <v-icon color="black">{{ item.icon }}</v-icon>
              {{ item.text }}
              <v-row class="my-2">
                <v-col>{{ item.datetime }}</v-col>
                <v-col>{{ item.company }}</v-col>
                <v-col>{{ item.position }}</v-col>
              </v-row>
              <p>{{ item.desc }}</p>
              <p class="text-subtitle-2">项目职责:</p>
              <p
                class="text-caption mb-2"
                v-for="(two, k) in item.content.todo"
                :key="k"
              >
                {{ two }}
              </p>
              <p class="text-subtitle-2 pt-2">项目业绩:</p>
              <p
                class="text-caption mb-2"
                v-for="(two, k) in item.content.done"
                :key="k"
              >
                {{ two }}
              </p>
            </v-alert>
          </v-card-text>
        </v-card>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  // 简易模式，大都以黑，白为主题
  name: 'ReMainEasy',
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
        desc: '超过10年自动化测试与开发经验，可以独立主导PC桌面、Web端、APP和基于协议的嵌入式软件的自动化测试的建设，拥有开发web网站和后端服务的经验。',
      },
      // 个人简介
      profile: [
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '独立开发RoWarlock自动化测试工具&管理系统',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '针对不同软件具有独立开发完整自动化测试工具&框架的经验',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '能够基于Vue.js框架，独立开发前端网站，拥有开发后端系统的经验',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '熟悉和擅长使用多种开源、闭源性自动化测试工具',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '熟悉和擅长设计、编写、测试用例; 针对现有测试用例体系提出建议、改进',
        },
        {
          icon: 'mdi-dots-horizontal-circle-outline',
          text: '具有一定的测试团队管理能力',
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
              '1.负责测试MTStar,ScaleManager两款上位机软件的功能测试;',
              '2.编写测试计划、测试用例和执行, 提交测试报告并汇总研发&测试最终文档;',
              '3.开发MTStar软件的自动化测试脚本与执行工具，搭建上位机与秤内交互操作的测试环境;',
              '4.负责PO&MO的售前、售后衔接工作; 针对不同区域的客户的需求进行售前、售后支持;',
              '5.参与秤内自动化测试工具维护和改进, 提供新工具与新脚本架构的Demo与设计思路;',
              '6.参与公司内部项目技术分享以及交流。',
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
              '1.参与云渲染平台的网站，后台管理网站，客户端和集群机的功能测试;',
              '2.参与和建设云渲染平台的自动化测试工具开发。',
            ],
          },
        },
        {
          icon: 'mdi-map-marker-circle',
          text: '测试主管、自动化测试工程师',
          content: {
            company: '无锡文思海辉',
            dept: '游戏基地、HP',
            datetime: '2011-02~2015-08',
            desc: '国内最大的离岸服务外包公司; 游戏基地为江苏移动的移动端手机游戏APP商城; 展讯为展讯芯片兼容与APP测试; HP为HP scan自动化工具开发和自动化测试',
            todo: [
              '1.负责管理游戏基地的团队、人员规划, 对测试工程师进行日常招聘、培训、任务分配、管理与考核;',
              '2.负责游戏基地的设备资产管理, 测试用例, 各类报表的统计与分析;',
              '3.负责游戏基地部门与各类学校的校企合作与兼职人员的绩效考核;',
              '4.参与HP团队的自动化测试脚本开发工作, 参与与印度、美国两地的测试工程师研发沟通',
              '5.负责HP scan的整体自动化测试架构, 领导、开发HP scan产品的自动化测试工作。',
            ],
          },
        },
      ],
      // 项目经历
      projects: [
        /**{
          icon: 'mdi-card-bulleted-outline',
          text: 'RoWarlock (PRO)',
          datetime: '2020-02~至今',
          company: '个人项目',
          position: '独立研发、测试',
          desc: 'RoWarlock是一个覆盖多端、包含全流程的现代化自动化测试工具。为客户提供一个具有可视化的，简易操作的重前端式的自动化测试工具。',
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
              '1.设计和完善系统的整体架构，包括系统的功能、模块、接口、数据库等;',
              '2.研发完整的Web前端的各个功能, 包含dashboard, 释放管理, 用例管理, 报告管理等; 使用vue.js+vuetify.js技术进行开发;',
              '3.研发完整的服务后端的各个功能，包含调度中心，任务管理器，通讯管理等; 使用.net c#技术进行开发;',
              '4.设计自动化测试脚本用例架构; 研发完整的自动化测试脚本执行工具，使用Typescript技术进行开发。',
            ],
            done: [
              '1.还在进行中;',
              '2.已完成前端EAP版本研发;',
              '3.已完成后端部分功能研发;',
              '4.已完成自动化测试脚本工具研发。',
            ],
          },
        },**/
        {
          icon: 'mdi-card-bulleted-outline',
          text: 'MTStar/Scale Manager',
          datetime: '2017-02~至今',
          company: '梅特勒 托利多 (商衡事业部)',
          position: '全栈测试工程师',
          desc: 'MTStar/Scale Manager为梅特勒托利多的商用衡器的PC端管理软件, 可以对电子秤进行数据管理, 秤管理, 秤设置等操作, 并可对秤进行远程操作与管理。并支持电子秤数据的导入导出进行计划管理。',
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
              '1.编写和执行上位机软件的功能测试用例;',
              '2.负责上位机软件的释放与管理;',
              '3.编写上位机软件的自动化测试脚本;',
              '4.编写上位机软件的自动化测试工具。',
            ],
            done: [
              '1.保障了MTStar/Scale Manager的产品质量，不断提高交付的效率; 全年流出BUG率为0;',
              '2.为客户提供多重的产品质量保障，为赢得客户订单提供了更多的产品优势, 包含多位客户因MTStar选择了我们的电子秤产品。',
            ],
          },
        },
        {
          icon: 'mdi-card-bulleted-outline',
          text: 'Archone TestTool',
          datetime: '2019-01~2019-08',
          company: '梅特勒 托利多 (商衡事业部)',
          position: '测试开发工程师',
          desc: 'Archone TestTool为梅特勒托利多的商用衡器的秤内自动化测试工具, 可以对电子秤进行基于协议的自动化测试。',
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
              '1.使用C++开发与改进Archone TestTool;',
              '2.针对原始Archone TestTool支持的xml脚本提出新想法;',
              '3.根据Archone平台的测试协议重新开发全流程工具与测试脚本, 使用Typescript与C#开发。',
            ],
            done: [
              '1.提升了测试工具的执行效率，提供更多的客户访问方法;',
              '2.为更新的测试工具与平台提供多重可改进的选择。',
            ],
          },
        },
        {
          icon: 'mdi-card-bulleted-outline',
          text: '赞奇云渲染平台测试',
          datetime: '2015-08~2017-02',
          company: '江苏赞奇科技有限公司',
          position: '自动化测试工程师工程师',
          desc: '赞奇云渲染平台是全国最大的云渲染平台，提供在线渲染静态图、效果图、动画、长动画等在线渲染服务。',
          content: {
            tech: ['功能测试', '.NET C#', 'Selenium', 'XML/XSD'],
            todo: [
              '1.参与赞奇云渲染平台的各个功能模块测试;',
              '2.负责赞奇云渲染平台的前台和后台管理网站的自动化测试。',
            ],
            done: [
              '1.保障了赞奇云渲染平台各个模块的释放质量;',
              '2.预研了赞奇云渲染平台中基于web的各个功能模块的自动化测试技术。',
            ],
          },
        },
        {
          icon: 'mdi-card-bulleted-outline',
          text: 'HP打印机与扫描机自动化测试',
          datetime: '2011-02~2013-08',
          company: '无锡文思海辉',
          position: '自动化测试开发工程师',
          desc: 'HP是全球最大的打印机和扫描机生产商，文思海辉HP团队整体负责HP全球的打印机与扫描机的新产品测试',
          content: {
            tech: ['Powershell', '.NET C#', 'Calabash', 'Cucumber', 'Ruby'],
            todo: [
              '1.参与HP打印机的自动化测试工作，基于HP Topcat自动化测试工具和VMPS执行工具进行自动化测试脚本编写和执行;',
              '2.负责HP扫描机的手机APP端自动化测试工作，基于Cucumber测试框架开发APP端自动化测试工具和测试脚本架构;',
              '3.协调印度与美国的HP扫描机团队的测试工作，统一规划整个团队的自动化测试工作。',
            ],
            done: [
              '1.从零开始搭建了HP扫描机团队的APP自动化测试体系;',
              '2.为HP的打印机新产品提供了有力的质量保障;',
              '3.为HP上海团队提供了Topcat工具改进的新方法;包含移动端和web端的自动化测试。',
            ],
          },
        },
        {
          icon: 'mdi-card-bulleted-outline',
          text: '游戏基地',
          datetime: '2011-02~2013-08',
          company: '无锡文思海辉',
          position: '测试主管',
          desc: '游戏基地是江苏移动主营的手机端游戏APP商城，提供手机游戏下载、付费和充值等服务。',
          content: {
            tech: ['Powershell', '.NET C#', 'Calabash', 'Cucumber', 'Ruby'],
            todo: [
              '1.负责管理游戏基地项目组日常工作，包含行政管理和业务管理两部分;',
              '2.负责采购和管理游戏基地使用的手机以及硬件设备，包含超过300款不同类型的手机;',
              '3.负责协同同PM下多个不同项目组的任务协调工作，包含手机借阅，人员流动和新项目的项目组建立。',
            ],
            done: [
              '1.保障了江苏移动的游戏基地内超过数万款的上线游戏的产品质量;',
              '2.为客户提供了7*24小时的产品质量保证服务;为部分客户挽回了大量因付费问题产生的异常流水资金。',
            ],
          },
        },
      ],
    };
  },
  methods: {
    /**
     * 更改显示模式
     */
    changeToSample() {
      this.$emit('changeToSample', false);
    },
  },
};
</script>

<style scoped></style>
