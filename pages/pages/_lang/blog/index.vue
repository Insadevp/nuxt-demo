<template>
<div class="Archive-page">
  <h1>mon archive</h1>

  <div class="list">
    <div class="card" v-for="(item, index) in articlesData" :key="index">
      <h2>{{ item.data.title[0].text }}</h2>
      <nuxt-link :to="`/fr-fr/blog/${item.id}`" >Voir article</nuxt-link>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'Archive',
  // On peut renseigner un layout par page, si aucun n'est renseigné, le layout "default.vue" est utilisé si existant
  layout: 'archive',
  async asyncData ({ $prismic, params, error }) {
    const articles = await $prismic.api.query(
      $prismic.predicates.at('document.type', 'articles'),
      { lang: params.lang }
    )
    const articlesData = articles.results

    return {
      articlesData
    }
  }
}
</script>

<style scoped>
.list {
  background: lightgrey;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
}

.card {
  height: 500px;
  width: 200px;
  background: white;
  box-shadow: 4px 4px 20px rgba(0, 0, 0, .3);
}
</style>
