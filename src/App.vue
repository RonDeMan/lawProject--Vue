<template>
  <v-app>
    <v-main class="Page-padding" style="direction:rtl">
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import { mapActions } from 'vuex';

import {getQuestions} from './DL/questions.js'


export default {
  name: 'App',

  data: () => ({
    //
  }),

  async created(){
    getQuestions().then((res) => this.setQuestions(res))
  },

  methods:{
    ...mapActions(["setQuestions"])
  }
};
</script>
<style scoped>
  .Page-padding{
    margin: 3rem;
  }
</style>
<style>
  .v-label{
    left:auto !important;
    right:1rem !important
  }
</style>