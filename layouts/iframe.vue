<template>
  <div class="text-center">
    <main>
      <nuxt />
    </main>
    <Source />
  </div>
</template>
<script>
import Source from '~/components/Source'

export default {
  components: {
    Source
  }
}
</script>
<style scoped>
html {
  @apply bg-white;
}
</style>
