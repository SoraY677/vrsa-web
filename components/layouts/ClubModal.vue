<template>
  <div>
    <v-dialog v-model="isShow" persistent>
      いｗ－やｗ－さｗーさｗー
      <v-btn @click="isShow = false" text></v-btn>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShow: false
    };
  },
  methods: {
    open() {
      this.isShow = true;
      console.log("open b");
    }
  }
};
</script>

<style></style>
