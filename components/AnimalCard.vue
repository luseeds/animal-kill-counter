<template>
  <div
    class="group hover:shadow-xl max-w-sm rounded overflow-hidden shadow-lg bg-gray-100 mx-auto sm:mx-0"
  >
    <img
      class="w-full h-40 object-cover"
      :src="require(`@/assets/img/${uid}.png`)"
      :alt="name"
    />
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-1">{{ count.toLocaleString() }}</div>
      <div class="text-base uppercase tracking-tight font-bold text-gray-600">
        {{ name }}
      </div>
      <p
        class="text-sm mt-2 tracking-tight font-bold text-gray-600 opacity-0 group-hover:opacity-100"
      >
        {{ killPerSecond }} killed every seconds
      </p>
    </div>
  </div>
</template>
<script>
const UPDATES_PER_SECONDS = 20
const SECONDS_PER_YEAR = 365 * 24 * 60 * 60
const INTERVAL = 1000 / UPDATES_PER_SECONDS

export default {
  props: {
    uid: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    number: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      updateCount: 0,
      count: 0
    }
  },
  computed: {
    killPerSecond() {
      const kills = Math.round(this.number / SECONDS_PER_YEAR)
      return kills === 0 ? '< 1' : kills.toLocaleString()
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
      this.count = Math.round(
        (intervalCount * (this.number / SECONDS_PER_YEAR)) / UPDATES_PER_SECONDS
      )
    },
    selfCorrectingTimeoutInterval() {
      this.updateCount += 1
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
<style></style>
