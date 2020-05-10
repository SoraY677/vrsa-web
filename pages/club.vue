<template>
  <div class="club">
    <Contents :content="content" />
    <v-row>
      <v-col cols="12" sm="12" md="4">
        <v-select
          v-model="selectDefault.campus"
          :items="filterWords.campus"
          prepend-icon="mdi-map-marker"
          label="キャンパス"
        >
        </v-select>
      </v-col>
      <v-col cols="12" sm="12" md="4">
        <v-select
          v-model="selectDefault.affiliation"
          :items="filterWords.affiliation"
          prepend-icon="fa-users"
          label="所属"
        ></v-select>
      </v-col>
      <v-col cols="12" sm="12" md="4">
        <v-select
          v-model="selectDefault.tag"
          :items="filterWords.tag"
          prepend-icon="fa-tags"
          label="タグ"
        ></v-select>
      </v-col>
    </v-row>
    <v-row class="d-flex justify-space-start">
      <v-col
        v-for="cardLine in clubCardList"
        :key="cardLine.index"
        cols="12"
        sm="6"
        md="4"
        lg="4"
        xl="4"
      >
        <ClubCard :content="cardLine" />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import Contents from "~/components/layouts/Contents.vue";
import ClubCard from "~/components/layouts/ClubCard";
export default {
  head() {
    return {
      title:
        this.content.title +
        " | TCU vRSA - 都市大非公認学生リモートサポートチーム",
      meta: [
        {
          hid: "description",
          name: "description",
          content:
            "東京都市大学非公認・リモート学生アシスタントチーム「vRSA」の公式Webサイトです。"
        },
        {
          hid: "og:title",
          name: "og:title",
          content:
            this.content.title +
            " | TCU vRSA - 都市大非公認学生リモートサポートチーム"
        },
        { hid: "og:url", name: "og:url", content: "https://tcu-vrsa.net/club" },
        { hid: "og:type", name: "og:type", content: "website" },
        {
          hid: "og:description",
          name: "og:description",
          content:
            "東京都市大学非公認・リモート学生アシスタントチーム「vRSA」の公式Webサイトです。"
        },
        {
          hid: "og:image",
          property: "og:image",
          content: "https://tcu-vrsa.net/img/ogp.png"
        },
        {
          hid: "twitter:card",
          name: "twitter:card",
          content: "summary_large_image"
        },
        {
          hid: "og:site_name",
          property: "og:site_name",
          content: "TCU vRSA - 都市大非公認学生リモートサポートチーム"
        },
        { hid: "og:locale", property: "og:locale", content: "ja_JP" }
      ]
    };
  },
  components: {
    Contents,
    ClubCard
  },
  data() {
    return {
      clubCardList: [
        {
          name: "arte",
          category: "同好会連合",
          affiliation: "横浜キャンパス",
          place: "32C",
          activityDay: "月・木・金 17:00~",
          imgpath: "/img/arte.jpg",
          description:
            "これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。これはテスト文章です。",
          tags: ["創作サークル", "うんたらかんたら"],
          link: {
            twitter: "https://twitter.com/ke_odakyu9000",
            hp: "https://arteofficial.web.fc2.com/why.html",
            hoge: "https://arteofficial.web.fc2.com/why.html"
          }
        },
        {
          name: "freaks",
          affiliation: "横浜キャンパス",
          place: "横浜キャンパスどこか",
          activityDay: "毎週2日",
          imgpath: "/img/Freaks.jpg",
          description: "test",
          tags: ["testtag", "testtag"],
          link: {}
        }
      ],
      filterWords: {
        campus: [
          "指定なし",
          "世田谷キャンパス",
          "横浜キャンパス",
          "等々力キャンパス"
        ],
        affiliation: [
          "指定なし",
          "学生団体連合会",
          "特殊団体",
          "文化団体連合会",
          "体育会",
          "同好会連合",
          "愛好会",
          "学科研究連合会"
        ],
        tag: [
          "指定なし",
          "学生団体",
          "音楽系",
          "情報系",
          "スポーツ",
          "球技",
          "武道",
          "文化・創作",
          "音響・撮影",
          "環境活動",
          "インドア",
          "アウトドア",
          "がっつり",
          "まったり",
          "大人数",
          "少人数",
          "合宿あり"
        ]
      },
      selectDefault: {
        campus: "指定なし",
        affiliation: "指定なし",
        tag: "指定なし"
      }
    };
  },
  async asyncData({ app }) {
    const response = await app.$axios.$get("https://api.tcu-vrsa.net/pages/3");
    return {
      content: response
    };
  },
  beforeUpdate() {}
};
</script>

<style>
</style>
