<template>
  <div class="container">
    <div>
      <nuxt-link to="/" class="inline-block">
        <h1 class="title">Animal Kill Counter</h1>
      </nuxt-link>
      <h2 class="subtitle">
        Witness the numbers of animal killed every seconds
      </h2>
      <section
        class="text-gray-800 mt-8 p-4 max-w-4xl mx-auto bg-gray-300 border-l-4 border-gray-600 rounded"
      >
        <div>
          Every seconds of every day, animals are being exploited, abused and
          killed only to please our taste buds, make some of our clothes,
          entertain ourselves or for testing purposes.
        </div>
        <div>
          There is no moral justification behind that, especially in our time
          and days where alternatives are widely available.
        </div>
        <br />
        <div>
          These numbers are so high that it's almost impossible to get a sense
          of them.
        </div>
        <div>
          They do not include the millions of animals killed in laboratories,
          fur farms, animal shelters, zoos, marine parks, or circuses. Nor do
          they include the animals killed by human negligence, blood sports,
          abuse, or extermination attempts.
        </div>
        <br />
        <div>
          We should always remember that we are talking about unique sentient
          living beings and that every life matters.
        </div>
        <div>
          Below you can witness the number of animals being: Killed. Every.
          Seconds.
        </div>
      </section>
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

.subtitle {
  @apply font-medium text-gray-600;
}
</style>
