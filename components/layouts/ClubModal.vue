<template>
  <v-dialog color="white" v-model="isShow">
    <v-card>
      <v-container style="position:relative; max-width:90%">
        <v-btn
          color="blue"
          absolute
          dark
          right
          fab
          @click="isShow = false"
          text
          x-large
        >
          <v-icon>mdi-close</v-icon>
          <div>close</div>
        </v-btn>
        <v-card-title class="display-1 text--primary">
          {{ content.name }}
        </v-card-title>
        <v-card-subtitle>{{ content.genre }}</v-card-subtitle>
        <!--リンク集-->
        <v-card-actions>
          <v-btn
            v-for="(value, key) in content.link"
            :key="key"
            @click="transLink(value)"
            text
          >
            <v-icon>{{ iconPathList[key] }}</v-icon>
          </v-btn>
        </v-card-actions>
        <v-divider></v-divider>
        <v-container>
          <!-- パンフ画像 -->
          <v-img
            class="mx-auto"
            :max-width="imgMaxSize"
            width="100%"
            height="100%"
            :src="content.imgpath"
          >
          </v-img>
          <p>{{ content.overview }}</p>
        </v-container>
      </v-container>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: {
    content: {}
  },
  data() {
    return {
      isShow: false,
      iconPathList: {
        hp: "fas fa-home",
        twitter: "fab fa-twitter"
      },
      imgMaxSize: ""
    };
  },
  created() {
    let img = new Image();
    img.src = this.content.imgpath;
    if (img.width < img.height) {
      this.imgMaxSize = "400px";
    } else {
      this.imgMaxSize = "100%";
    }
  },
  methods: {
    transLink(path) {
      window.open(path, "_blank");
    },
    open() {
      this.isShow = true;
    }
  }
};
</script>

<style></style>
