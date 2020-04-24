<template>
  <div class="club">
    <Contents :content="content"/>
    <section>
    <h2>SC団体</h2>
    <ul class="club-card-list">
    <li><clubcard /></li>
    <li><clubcard /></li>
    <li><clubcard /></li>
    <li><clubcard /></li>
    </ul>
    </section>
    <section>
    <h2>YC団体</h2>
    </section>
    <section>
    <h2>TC団体</h2>
    </section>    
  </div>
</template>

<script>
import Contents from '~/components/layouts/Contents.vue';
import clubcard from '~/components/layouts/ClubCard'
export default {
  head() {
    return {
      title: this.content.title + ' | TCU vRSA - 都市大非公認学生リモートサポートチーム',
      meta: [
        { hid: 'description', name: 'description', content: '東京都市大学非公認・リモート学生アシスタントチーム「vRSA」の公式Webサイトです。' },
        { hid: 'og:title', name: 'og:title', content: this.content.title + ' | TCU vRSA - 都市大非公認学生リモートサポートチーム' },
        { hid: 'og:url', name: 'og:url', content: 'https://tcu-vrsa.net/club' },
        { hid: 'og:type', name: 'og:type', content: 'website' },
        { hid: 'og:description', name: 'og:description', content: '東京都市大学非公認・リモート学生アシスタントチーム「vRSA」の公式Webサイトです。' },
        { hid: 'og:image', property: 'og:image', content: 'https://tcu-vrsa.net/img/ogp.png' },
        { hid: 'twitter:card', name: 'twitter:card', content: 'summary_large_image' },
        { hid: 'og:site_name', property: 'og:site_name', content: 'TCU vRSA - 都市大非公認学生リモートサポートチーム' },
        { hid: 'og:locale', property: 'og:locale', content: 'ja_JP' },
      ]
    }
  },
  components: {
    Contents,
    clubcard
  },
  async asyncData({ app }) {
    const response = await app.$axios.$get('https://api.tcu-vrsa.net/pages/3');
    return {
      content: response
    };
  }
}
</script>

<style>

ul.club-card-list{
  display: flex;
  padding:0;
  margin:0;
  justify-content: space-between;
  flex-wrap: wrap;
  list-style: none;
}

ul.club-card-list > li{
  width:33%;
  padding:1%;
}

</style>