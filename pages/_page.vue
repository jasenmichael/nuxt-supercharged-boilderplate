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
  middleware({ redirect, route }) {
    route.path == '/home' && redirect('/')
  },
  async asyncData({ $content, params }) {
    const page = await $content(`pages/${params.page || 'home'}`)
      .fetch()
      // .catch(err => {
      //   return Error({ statusCode: 404, message: "Page not found" });
      // });
    return {
      page,
      params,
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
        type: 'website', // use article for blogs and articless
        title: this.page.title,
        description: this.page.description,
        url: this.canonicalUrl,
        mainImage:
          ((this.$config.ngrok && this.$config.ngrok.url) ||
            this.$config.baseUrl) + (this.page.cover || '/img/og-share.png'),
      }
      return getMeta(metaData)
    },
  },
  head() {
    return {
      title: this.page.title,
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
