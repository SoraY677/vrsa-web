<template>
  <v-dialog color="white" v-model="isShow">
    <v-card>
      <v-container style="max-width:90%;">
        <v-app-bar color="white" elevation="0">
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

        <div class="d-flex">
          <v-avatar size="120" tile>
            <v-img :src="content.icon"></v-img>
          </v-avatar>

          <p>
            <v-card-title class=" display-1 text--primary">
              {{ content.name }}
            </v-card-title>
            <v-card-subtitle>{{ content.category }}</v-card-subtitle>
          </p>
          <v-divider vertical inset></v-divider>
          <!--リンク集-->
          <v-card-actions class="d-flex flex-column">
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
        </div>
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
          <v-chip v-for="tag in content.tags" :key="tag.id" class="ma-2" label>
            {{ tag }}
          </v-chip>
        </v-chip-group>

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
