<template>
  <div>
    <BannerComp />
    <p>Home page</p>
    <div ref="testimonialSlider" class="swiper-container">
      <ul class="list swiper-wrapper">
        <li class="item swiper-slide">1</li>
        <li class="item swiper-slide">2</li>
        <li class="item swiper-slide">3</li>
      </ul>
    </div>

    <div class="nav-wrap">
      <div ref="prevBtn" class="prev swiper-button-prev">left</div>
      <div ref="nextBtn" class="next swiper-button-next">right</div>
    </div>
  </div>
</template>

<script>
import Swiper, { Navigation } from 'swiper'

Swiper.use([Navigation])

export default {
  name: 'IndexPage',
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
      STORE: this.$store.state?.home,
    })

    this.initTestimonSlider()
  },
  methods: {
    initTestimonSlider() {
      const testimonSlider = new Swiper(this.$refs.testimonialSlider, {
        loop: true,
        navigation: {
          nextEl: this.$refs.prevBtn,
          prevEl: this.$refs.nextBtn,
        },
      })

      testimonSlider.init()

      this.$once('hook:beforeDestroy', () => {
        testimonSlider.destroy()
      })
    },
  },
}
</script>

<style>
p {
  color: green;
}

.item {
  padding: 3rem;
  background-color: beige;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
