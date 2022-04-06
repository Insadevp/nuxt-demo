<template>
  <div class="home">
    <h1>{{ homepageData.title[0].text }}</h1>

    <div class="banner-container">
      <img :src="homepageData.banner.url" alt="" />
    </div>
    <!-- On peut utiliser les composants sans faire les import au préalable dans la section script -->
    <Button> Test du slot </Button>

    <!-- Si on fait un sous-dossier dans le dossier composant, on peut accéder à celui-ci en camelCase
    => ici input.vue est dans le dossier "forms" => on écrit FormsInput pour appeler le composant -->
    <FormsInput />
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  async asyncData({ $prismic, params, error }) {
    const homepage = await $prismic.api.getSingle("Homepage");
    const homepageData = homepage.data;

    return {
      homepageData,
    };
  },
};
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
