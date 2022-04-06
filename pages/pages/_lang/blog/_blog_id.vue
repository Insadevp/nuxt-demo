<template>
  <div class="article">
    <h1>{{ result.data.title[0].text }} actualisé</h1>

    <div class="banner-container">
      <img :src="result.data.banner.url" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Article',
  async asyncData ({ $prismic, params, error }) {
    const result = await $prismic.api.getByID(params.blog_id)

    return {
      result
    }
  },
  data () {
    return {
      title: 'Test article :'
    }
  },
  created() {
   console.log('created')
  },
  mounted() {
    console.log('mounted')
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
