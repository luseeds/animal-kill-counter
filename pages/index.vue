<template>
  <div class="container">
    <div>
      <nuxt-link to="/" class="inline-block">
        <h1 class="title">Animal Kill Counter</h1>
      </nuxt-link>
      <h2 class="sub-title">
        Witness the numbers of animal killed every seconds
      </h2>
      <animal-cards />
    </div>
  </div>
</template>

<script>
import AnimalCards from '~/components/AnimalCards.vue'

export default {
  components: {
    AnimalCards
  },
  head() {
    return {
      title: 'Animal Kill Counter - luseeds',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Witness the numbers of animal killed every seconds'
        }
      ]
    }
  }
}
</script>

<style>
.container {
  @apply my-0 mx-auto text-center;
}

.title {
  @apply text-4xl font-medium text-gray-800;
}

.sub-title {
  @apply font-medium text-gray-600;
}
</style>
