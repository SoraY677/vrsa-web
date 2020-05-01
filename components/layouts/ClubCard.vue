<template>
  <v-card class="fill-height" @click="openModal()">
    <!-- タイトル -->
    <v-card-title>
      {{ content.name }}
    </v-card-title>
    <v-card-subtitle>
      {{ content.genre }}
    </v-card-subtitle>
    <v-img height="200px" :src="content.imgpath"> </v-img>
    <!--リンク集-->
    <!-- <v-card-actions>
      <v-btn
        v-for="(value, key) in content.link"
        :key="key"
        @click="transLink(value)"
        text
      >
        <v-icon>{{ iconPathList[key] }}</v-icon>
      </v-btn>
    </v-card-actions> -->
    <ClubModal ref="club_modal" :content="content" />
  </v-card>
</template>

<script>
import ClubModal from "~/components/layouts/ClubModal";

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
  components: {
    ClubModal
  },
  methods: {
    transLink(path) {
      window.open(path, "_blank");
    },
    openModal() {
      this.$refs.club_modal.open();
    }
  }
};
</script>

<style></style>
