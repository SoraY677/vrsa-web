<template>
  <div class="club-card">
    <v-card class="mx-auto" outlined>
      <v-img
        height="200"
        padding="2%"
        class="white--text align-end"
        src="https://pbs.twimg.com/profile_images/1272197668/stoyc_400x400.jpg"
        float="left"
      ></v-img>

      <v-card-title class="pb-0">横浜分室</v-card-title>

      <v-card-text class="text--primary">
        <p>
          横浜分室の説明文だよ～～～～～ほげほげおｈごえげほげおｇへｗｈごえおがをえｈふぉいあｈふぇわおｇふあえｒふｇふおらわあああああああああああああああああああああああああああああああああああああああああああ(100文字)
        </p>
      </v-card-text>
      <v-card-actions>
        <v-btn href="https://twitter.com/YCbunsitsu" target="_blank" text>
          <v-icon>fab fa-twitter</v-icon>
        </v-btn>
        <v-btn href="https://twitter.com/YCbunsitsu" target="_blank" text>
          <v-icon>fab fa-twitter</v-icon>
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: true
    };
  }
};
</script>

<style></style>
