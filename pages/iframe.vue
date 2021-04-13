<template>
  <div class="container">
    <div>
      <animal-cards />
      <div class="pt-8">
        A project by
        <a
          href="https://luseeds.com"
          class="text-green-800 hover:text-green-500"
          >luseeds</a
        >
      </div>
      <div>
        See the full project on
        <a
          href="https://animal-kill-counter.luseeds.com"
          class="text-green-800 hover:text-green-500"
          >Animal Kill Counter</a
        >
      </div>
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
  },
  layout: 'iframe'
}
</script>

<style>
.container {
  @apply my-0 mx-auto text-center;
}
</style>
