<template>
  <div class="case-studies">
    <h1 class="case-title">Voici mes cas clients</h1>

    <div class="case-list">
      <div class="card" v-for="(item, index) in studiesData" :key="index">
        <p>
          {{ item.data.title[0].text }}
        </p>

        <nuxt-link :to="`/fr-fr/cases/${item.id}`">
          voir le case d'étude
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ArchiveCaseStudies",
  async asyncData({ $prismic, params, error }) {
    const caseStudies = await $prismic.api.query(
      $prismic.predicates.at("document.type", "case-studies")
    );

    const studiesData = caseStudies.results;

    return {
      studiesData,
    };
  },
};
</script>

<style scoped>
.case-studies {
}

.case-title {
  font-size: 40px;
  margin-bottom: 50px;
}

.case-list {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.card {
  justify-self: center;
  padding: 30px;
  background: white;
}
</style>
