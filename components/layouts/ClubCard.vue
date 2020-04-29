<template>
  <v-card class="fill-height">
    <!-- タイトル -->
    <v-card-text>
      <p>●●団体</p>
      <p class="display-1 text--primary">
        {{ content.name }}
      </p>
    </v-card-text>
    <!--リンク集-->
    <v-card-actions>
      <v-btn v-if="!Object.keys(content.link).length" disabled text></v-btn>
      <v-btn
        v-for="(value, key) in content.link"
        :key="key"
        @click="transLink(value)"
        text
      >
        <v-icon>{{ iconPathList[key] }}</v-icon>
      </v-btn>
    </v-card-actions>
    <!-- 説明文 -->
    <v-card-text class="text--primary">
      {{ content.overview }}
    </v-card-text>
  </v-card>
  <!-- <div class="container fill-height">
    <v-card class="layout" outlined>
      <v-container fluid>

        <v-card-title class="pb-0">{{ content.name }}</v-card-title>

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
        <v-card-text class="text--primary">
          {{ content.overview }}
        </v-card-text>
      </v-container>
    </v-card>
  </div> -->
</template>

<script>
export default {
  props: {
    content: Object
  },
  data() {
    return {
      iconPathList: {
        hp: "fas fa-home",
        twitter: "fab fa-twitter"
      }
    };
  },
  methods: {
    transLink(path) {
      window.open(path, "_blank");
    }
  }
};
</script>

<style></style>
