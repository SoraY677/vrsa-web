<template>
  <v-dialog color="white" v-model="isShow" max-width="1000px">
    <v-card class="px-10">
      <v-container>
        <v-app-bar class="mb-3" color="white" elevation="0">
          <v-spacer></v-spacer>
          <v-btn
            color="blue"
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
        </v-app-bar>

        <v-card class="mx-auto" max-width="800px" elevation="0">
          <p>
            <v-card-title class=" display-1 text--primary">
              {{ content.name }}
            </v-card-title>
            <v-card-subtitle>{{ content.category }}</v-card-subtitle>
          </p>
          <v-chip-group column>
            <v-chip class="ma-2" color="blue" outlined>
              <v-icon left>mdi-domain </v-icon>
              {{ content.affiliation }}
            </v-chip>
            <v-chip class="ma-2" color="blue" outlined>
              <v-icon left>mdi-map-marker </v-icon>
              {{ content.place }}
            </v-chip>
            <v-chip class="ma-2" color="blue" outlined>
              <v-icon left>mdi-calendar-blank-outline </v-icon>
              {{ content.activityDay }}
            </v-chip>
          </v-chip-group>
          <v-chip-group column>
            <v-chip
              v-for="tag in content.tags"
              :key="tag.id"
              class="ma-2"
              label
            >
              {{ tag }}
            </v-chip>
          </v-chip-group>
          <!--リンク集-->
          <v-card-actions class="d-flex">
            <v-btn
              class="pt-2"
              v-for="(value, key) in content.link"
              :key="key"
              @click="transLink(value)"
              text
            >
              <v-icon>{{ iconPathList[key] }}</v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
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
        </v-container>
        <v-divider></v-divider>
        <p>{{ content.description }}</p>
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
        twitter: "fab fa-twitter",
        hoge: "hoge"
      },
      imgMaxSize: ""
    };
  },
  created() {
    let img = new Image();
    img.src = this.content.imgpath;
    if (img.width < img.height) {
      this.imgMaxSize = "600px";
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
