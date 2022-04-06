<template>
  <div class="Archive-page">
    <h1>mon archive</h1>
    <div class="list">
      <div class="card" v-for="(item, index) in articlesData" :key="index">
        <h2>{{ item.data.title[0].text }}</h2>
        <nuxt-link :to="`/blog/${item.id}`">voir article</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Archive",
  // On peut renseigner un layout par page, si aucun n'est renseigné, le layout "default.vue" est utilisé si existant
  layout: "archive",
  async asyncData({ $prismic, params, error }) {
    const articles = await $prismic.api.query(
      $prismic.predicates.at("document.type", "articles")
    );
    const articlesData = articles.results;
    return {
      articlesData,
    };
  },
};
</script>
