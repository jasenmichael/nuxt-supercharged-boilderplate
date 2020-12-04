<template>
  <div>
    <h1>{{ page.title }}</h1>
    <h2>{{ page.description }}</h2>
    <nuxt-content :document="page" />
  </div>
</template>


<script>
import getMeta from '~/utils/getMeta.js'
export default {
  async asyncData({ $content }) {
    const page = await $content('pages/home').fetch()
    return {
      page,
    }
  },
  computed: {
    canonicalUrl() {
      return (
        ((this.$config.ngrok && this.$config.ngrok.url) ||
          this.$config.baseUrl) + this.$route.fullPath
      )
    },
    meta() {
      const metaData = {
        type: 'website', // use article for blogs and such
        title: this.$config.siteData.name,
        description: this.$config.siteData.description,
        url: this.canonicalUrl,
        mainImage:
          ((this.$config.ngrok && this.$config.ngrok.url) ||
            this.$config.baseUrl) + (this.page.cover || '/og-share.png'),
      }
      return getMeta(metaData, this.$config.siteData, this.canonicalUrl)
    },
  },
  head() {
    return {
      title: this.page.description,
      meta: this.meta,
      link: [
        {
          hid: 'canonical',
          rel: 'canonical',
          href: this.canonicalUrl,
        },
      ],
    }
  },
}
</script>
