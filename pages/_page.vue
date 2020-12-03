<template>
  <div>
    <h5>Canonical: {{ canonicalUrl }}</h5>
    <h1>{{ page.title }}</h1>
    <h2>{{ page.description }}</h2>
    params: {{ params.page || 'home' }}
    <!-- <img src="" alt=""> -->
    <nuxt-content :document="page" />
    <pre>Path: {{ $route.fullPath }}</pre>
    <hr />
    Page Data:
    <pre>
      {{ page }}
    </pre>
    <hr />
    Config:
    <pre>{{ $config }}</pre>
  </div>
</template>


<script>
import getMeta from '~/utils/getMeta.js'
export default {
  middleware({ redirect, route }) {
    route.path == '/home' && redirect('/')
  },
  async asyncData({ $content, params }) {
    const page = await $content(`pages/${params.page || 'home'}`).fetch()
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
            this.$config.baseUrl) + (this.page.cover || '/og-share.png'),
      }
      return getMeta(metaData, this.$config.siteData, this.canonicalUrl)
    },
  },
  head() {
    return {
      title: this.page.title,
      meta: [
        ...this.meta,
        {
          hid: 'og:url',
          property: 'og:url',
          content: this.canonicalUrl,
        },
      ],
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
