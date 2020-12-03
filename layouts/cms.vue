<template>
  <div>
    <a :href="homeUrl">
      Go back to
      <h1>{{ homeUrl }}</h1>
    </a>
    <v-container>
      <nuxt />
    </v-container>
  </div>
</template>



<script>
export default {
  computed: {
    homeUrl() {
      return (
        (this.$config.ngrok && this.$config.ngrok.url) || this.$config.baseUrl
      )
    },
  },
}
</script>
