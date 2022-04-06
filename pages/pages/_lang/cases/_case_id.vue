<template>
  <div class="case-study">
    <h1> Cas d'étude : {{ caseStudy.data.title[0].text }} </h1>
    <p>{{ caseStudy.data.desc[0].text }} </p>

  </div>
</template>

<script>
export default {
  name: 'CaseStudy',
    async asyncData ({ $prismic, params, error }) {
    const caseStudy = await $prismic.api.getByID(params.case_id )

    return {
      caseStudy
    }
  }
}
</script>
