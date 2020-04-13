<template>
  <div class="text-center">
    <nuxt-link to="/" class="inline-block" aria-label="go to homepage">
      <logo color="text-orange-900" :size="125" />
    </nuxt-link>
    <nuxt />
    <Source />
    <Footer />
  </div>
</template>
<script>
import Logo from '~/components/Logo.vue'
import Source from '~/components/Source'
import Footer from '~/components/Footer'

export default {
  components: {
    Logo,
    Source,
    Footer
  }
}
</script>
<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  @apply bg-gray-200;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

a {
  @apply text-orange-800;
}

a:hover {
  @apply text-orange-600;
}
</style>
