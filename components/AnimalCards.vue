<template>
  <div class="mt-8">
    <div class="text-lg text-gray-800">
      The counters started
      <span class="text-orange-700 font-bold">{{ timeElapsed }}</span> ago
    </div>
    <div class="grid sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4 m-8">
      <animal-card
        v-for="animal in animals"
        :key="animal.key"
        :uid="animal.key"
        :name="animal.name"
        :killed-per-second="animal.killedPerSecond"
        :killed="animal.killed"
      />
    </div>
  </div>
</template>
<script>
import AnimalCard from '~/components/AnimalCard.vue'

const UPDATES_PER_SECONDS = 20
const SECONDS_PER_YEAR = 365 * 24 * 60 * 60
const INTERVAL = 1000 / UPDATES_PER_SECONDS

const animals = [
  {
    key: 'wildCaughtFishes',
    name: 'Wild caught fishes',
    killPerYear: 970000000000
  },
  { key: 'chickens', name: 'Chickens', killPerYear: 61171973510 },
  { key: 'farmedFishes', name: 'Farmed fishes', killPerYear: 38000000000 },
  { key: 'ducks', name: 'Ducks', killPerYear: 2887594480 },
  { key: 'pigs', name: 'Pigs', killPerYear: 1451856889.38 },
  { key: 'rabbits', name: 'Rabbits', killPerYear: 1171578000 },
  { key: 'geese', name: 'Geese', killPerYear: 687147000 },
  { key: 'turkeys', name: 'Turkeys', killPerYear: 618086890 },
  { key: 'sheep', name: 'Sheep', killPerYear: 536742256.33 },
  { key: 'goats', name: 'Goats', killPerYear: 438320370.99 },
  { key: 'cattle', name: 'Cattle', killPerYear: 298799160.08 },
  { key: 'rodents', name: 'Rodents', killPerYear: 70371000 },
  { key: 'otherBirds', name: 'Other birds', killPerYear: 59656000 },
  { key: 'buffalos', name: 'Buffalos', killPerYear: 25798819 },
  { key: 'horses', name: 'Horses', killPerYear: 4863367 },
  { key: 'camels', name: 'Camels', killPerYear: 3243266.03 },
  { key: 'donkeys', name: 'Donkeys', killPerYear: 3213400 }
]

const addKilledPerSecondValue = (animal) => {
  const killedPerSecond = Math.round(animal.killPerYear / SECONDS_PER_YEAR)

  animal.killedPerSecond = killedPerSecond
    ? killedPerSecond.toLocaleString()
    : '< 1'
}

animals.forEach(addKilledPerSecondValue)

export default {
  components: {
    AnimalCard
  },
  data: () => ({
    updateCount: 0,
    secondsElapsed: 0,
    animals
  }),
  computed: {
    timeElapsed() {
      const minutes = Math.floor(this.secondsElapsed / 60)
      const seconds = this.secondsElapsed % 60
      let timeText = minutes
        ? `${minutes} minute${minutes === 1 ? '' : 's'} `
        : ''
      timeText += `${seconds} second${seconds === 1 ? '' : 's'}`

      return timeText
    }
  },
  mounted() {
    this.start = new Date().getTime()
    this.timeout = window.setTimeout(
      this.selfCorrectingTimeoutInterval,
      INTERVAL
    )
  },
  destroyed() {
    window.clearTimeout(this.timeout)
  },
  methods: {
    update(intervalCount) {
      this.animals = this.animals.map((animal) => ({
        ...animal,
        killed: Math.round(
          (intervalCount * (animal.killPerYear / SECONDS_PER_YEAR)) /
            UPDATES_PER_SECONDS
        )
      }))
    },
    selfCorrectingTimeoutInterval() {
      this.updateCount += 1
      this.secondsElapsed = Math.round(
        (new Date().getTime() - this.start) / 1000
      )
      this.update(this.updateCount)
      this.timeout = window.setTimeout(
        this.selfCorrectingTimeoutInterval,
        INTERVAL -
          (new Date().getTime() - this.start - this.updateCount * INTERVAL)
      )
    }
  }
}
</script>
