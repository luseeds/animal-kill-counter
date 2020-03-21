<template>
  <div class="container">
    <div>
      <nuxt-link to="/" class="inline-block"
        ><h1 class="title">Animal Kill Counter</h1></nuxt-link
      >
      <h2 class="sub-title">
        Show the numbers of animal being killed
      </h2>
      <div
        class="grid sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4 m-8 mx-4"
      >
        <animal-card
          v-for="animal in animals"
          :key="animal.key"
          :uid="animal.key"
          :name="animal.name"
          :number="animal.number"
        />
      </div>
    </div>
  </div>
</template>

<script>
import AnimalCard from '~/components/AnimalCard.vue'

export default {
  components: {
    AnimalCard
  },
  data: () => ({
    animals: [
      { key: 'wildCaughtFish', name: 'Wild caught fish', number: 970000000000 },
      { key: 'chicken', name: 'Chicken', number: 61171973510 },
      { key: 'farmedFish', name: 'Farmed fish', number: 38000000000 },
      { key: 'ducks', name: 'Ducks', number: 2887594480 },
      { key: 'pigs', name: 'Pigs', number: 1451856889.38 },
      { key: 'rabbits', name: 'Rabbits', number: 1171578000 },
      { key: 'geese', name: 'Geese', number: 687147000 },
      { key: 'turkeys', name: 'Turkeys', number: 618086890 },
      { key: 'sheep', name: 'Sheep', number: 536742256.33 },
      { key: 'goats', name: 'Goats', number: 438320370.99 },
      { key: 'cattle', name: 'Cattle', number: 298799160.08 },
      { key: 'rodents', name: 'Rodents', number: 70371000 },
      { key: 'otherBirds', name: 'Other birds', number: 59656000 },
      { key: 'buffalo', name: 'Buffalo', number: 25798819 },
      { key: 'horses', name: 'Horses', number: 4863367 },
      { key: 'camels', name: 'Camels', number: 3243266.03 },
      { key: 'donkeys', name: 'Donkeys', number: 3213400 }
    ]
  }),
  head() {
    return {
      title: 'Animal Kill Counter - luseeds',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'See the number of animal killed every seconds'
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
