<template>
  <v-app >
    <v-main >
      <div v-if="changesample===false">
        <rs-main @changeToSample="changeToSample"/>
      </div>
      <div v-else>
        <re-main-easy @changeToSample="changeToSample" />
      </div>
    </v-main>
  </v-app>
</template>
<script>
import RsMain from './components/RsMain';
import ReMainEasy from '@/components/ReMainEasy';
export default {
  name: 'App',
  components: {
    RsMain,
    ReMainEasy
  },

  data() {
    return {
      changesample:true
    };
  },
  methods: {
    /**
     * 更改显示模式
     * @param value
     */
    changeToSample(value){
      this.changesample=value;
    }
  }
};
</script>
