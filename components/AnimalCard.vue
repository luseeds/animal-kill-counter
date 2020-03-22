<template>
  <div
    class="group hover:shadow-xl max-w-sm rounded overflow-hidden shadow-lg bg-gray-100 mx-auto sm:mx-0"
  >
    <img
      class="w-full h-40 object-cover"
      :src="require(`@/assets/img/${uid}.jpg`)"
      :alt="name"
    />
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-1">{{ killed.toLocaleString() }}</div>
      <div class="text-base uppercase tracking-tight font-bold text-gray-600">
        {{ name }}
      </div>
      <p
        class="text-sm mt-2 tracking-tight font-bold text-gray-600 opacity-0 group-hover:opacity-100"
      >
        {{ killedPerSecond }} killed every seconds
      </p>
    </div>
  </div>
</template>
<script>
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
    killed: {
      type: Number,
      default: 0
    },
    killedPerSecond: {
      type: String,
      default: '0'
    }
  }
}
</script>
<style></style>
