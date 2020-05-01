<template>
  <v-card class="fill-height" @click="openModal()">
    <!-- タイトル -->
    <v-card-title>
      {{ content.name }}
    </v-card-title>
    <v-card-subtitle>
      {{ content.genre }}
    </v-card-subtitle>
    <v-container>
      <v-img height="200px" :src="content.imgpath"> </v-img>
    </v-container>
    <ClubModal ref="club_modal" :content="content" />
  </v-card>
</template>

<script>
import ClubModal from "~/components/layouts/ClubModal";

export default {
  props: {
    content: Object
  },
  components: {
    ClubModal
  },
  methods: {
    openModal() {
      this.$refs.club_modal.open();
    }
  }
};
</script>

<style></style>
