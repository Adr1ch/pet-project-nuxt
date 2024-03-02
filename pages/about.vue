<template>
  <div>
    <BannerComp />
    <p>About page</p>
  </div>
</template>

<script>
export default {
  name: 'AboutPage',
  head() {
    return {
      bodyAttrs: {
        class: this.$route.name === 'about' ? 'dark' : 'light',
      },
      title: 'my website title',
      meta: [
        { charset: 'utf-8' },
        { name: 'viewport', content: 'width=device-width, initial-scale=1' },
        {
          hid: 'description',
          name: 'description',
          content: 'my website description',
        },
      ],
      link: [{ rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }],
    }
  },
  mounted() {
    console.log({
      LOG_MESSAGE: 'Hello',
      STORE: this.$store.state?.about,
    })
  },
}
</script>
