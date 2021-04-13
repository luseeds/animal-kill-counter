<template>
  <section class="text-center text-gray-800 py-8">
    <button
      v-if="!expanded"
      class="bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
      @click="expanded = !expanded"
    >
      Source & Credits
    </button>
    <transition name="fade">
      <div v-if="expanded">
        <div class="text-lg uppercase mt-4 mb-2">Sources</div>
        <p>
          Number of land animal killed (2013)
          <a href="http://faostat3.fao.org/download/Q/QL/E">2013</a>
        </p>
        <p>
          Fish count estimates
          <a href="http://fishcount.org.uk/fish-count-estimates"
            >fishcount.org.uk</a
          >
        </p>
        <p>
          Inspired by
          <a href="http://considerveganism.com/counter/">considerveganism</a>
          counters
        </p>
        <div class="text-lg uppercase mt-4 mb-2">Credits</div>
        <p>
          Images are from
          <a href="https://unsplash.com">Unsplash</a>
        </p>
        <p>
          Logo is from
          <a href="https://www.vecteezy.com/free-vector/animal-skulls"
            >Vecteezy</a
          >
        </p>
      </div>
    </transition>
  </section>
</template>

<script>
export default {
  name: 'Source',
  data: () => ({
    expanded: false
  })
}
</script>
