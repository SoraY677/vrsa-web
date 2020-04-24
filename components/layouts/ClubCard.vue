<template>
  <div class="container fill-height">
    <v-card class="layout" outlined>
      <v-container fluid>
      <v-img
        height="250"
        class="white--text align-end"
        :src="content.imgpath"
        float="left"
      ></v-img>

      <v-card-title class="pb-0">{{ content.name }}</v-card-title>


      <v-card-actions >
        <v-btn v-for="(value,key) in content.link" :key="key" @click="transLink(value)" text>
          <v-icon>{{iconPathList[key]}}</v-icon>
        </v-btn>
      </v-card-actions>
      <v-card-text class="text--primary">
          {{ content.overview }}
        
      </v-card-text>
      </v-container>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {
    content: Object
  },
  data() {
    return {
      iconPathList: {
        hp:"fas fa-home",
        twitter:"fab fa-twitter"
      }
    };
  },
  methods:{
    transLink(path){
      window.open(path,"_blank")
    }
  }
};
</script>

<style>
</style>
