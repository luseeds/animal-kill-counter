<template>
  <div class="__nuxt-error-page">
    <div class="error">
      <nuxt-link to="/" class="inline-block" aria-label="go to homepage">
        <logo color="text-orange-900" :size="125" />
      </nuxt-link>

      <div class="title">{{ message }}</div>
      <p v-if="statusCode === 404" class="description">
        <NuxtLink class="error-link" to="/">Back to the home page</NuxtLink>
      </p>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  name: 'NuxtError',
  components: {
    Logo
  },
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  computed: {
    statusCode() {
      return (this.error && this.error.statusCode) || 500
    },
    message() {
      return this.error.message || '<%= messages.client_error %>'
    }
  },
  head() {
    return {
      title: this.message
    }
  }
}
</script>

<style>
.__nuxt-error-page {
  padding: 1rem;
  background: #f7f8fb;
  color: #47494e;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  font-family: sans-serif;
  font-weight: 100 !important;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -webkit-font-smoothing: antialiased;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
.__nuxt-error-page .error {
  max-width: 450px;
}
.__nuxt-error-page .title {
  font-size: 1.5rem;
  margin-top: 15px;
  color: #47494e;
  margin-bottom: 8px;
}
.__nuxt-error-page .description {
  color: #7f828b;
  line-height: 21px;
  margin: 16px 0;
}
.__nuxt-error-page a {
  color: #7f828b !important;
  text-decoration: none;
}
</style>
