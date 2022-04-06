<template>
  <h1>page de chargement</h1>
</template>

<script>
import { mapState } from 'vuex'

export default {
  name: 'SplashScreen',
  computed: {
    ...mapState([
      'lang'
    ])
  },
  methods: {
    redirect() {
      this.$router.push(`/${this.lang}/`)
    }
  },
  created() {
      this.redirect()
  }
}
</script>
