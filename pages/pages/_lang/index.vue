<template>
  <div class="home">
    <h1>{{ homepageData.title[0].text }} actualisé</h1>
    <!-- <prismic-rich-text :field="homepageData.title[0].text" /> -->

    <div class="banner-container">
      <img :src="homepageData.banner.url" alt="">
    </div>
    <!-- On peut utiliser les composants sans faire les import au préalable dans la section script -->
    <Button>
      Test du slot
    </Button>

    <!-- Si on fait un sous-dossier dans le dossier composant, on peut accéder à celui-ci en camelCase
    => ici input.vue est dans le dossier "forms" => on écrit FormsInput pour appeler le composant -->
    <FormsInput/>

    <Card>
      <h2> Titre niveau 2</h2>
      <p>description de la section</p>
      <div class="banner-container">
        <img :src="homepageData.banner.url" alt="">
      </div>
    </Card>

    <div class="content" v-if="homepageData.content">
      <prismic-rich-text :field="homepageData.content" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Homepage',
  async asyncData ({ $prismic, params, error }) {
    const homepage = await $prismic.api.getSingle('homepage', { lang: params.lang })
    const homepageData = homepage.data

    return {
      homepageData
    }
  }
}
</script>

<style scoped>
  .banner-container {
    width: 100%;
    height: 40vh;
  }

  .banner-container img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
</style>
