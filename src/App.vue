<template>
  <v-app >
    <v-main >
      <rs-main />
    </v-main>
  </v-app>
</template>
<script>
import RsMain from './components/RsMain';
export default {
  name: 'App',
  components: {
    RsMain,
  },

  data() {
    return {};
  },
};
</script>
