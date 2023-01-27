<template>
  <div class="mb-2 md:mb-4 flex items-center w-full px-2 pb-1 border-b border-solid border-gray-400">
    <div>
      <p class="text-gray-700 md:text-sm text-xs">{{ date }}</p>
    </div>
    <div class="md:ml-14 ml-3 md:mr-6">
      <div class="inline-block custom-bg rounded-md text-white px-2 py-1">
        <p class="md:text-sm text-xs">{{ type }}</p>
      </div>
    </div>
    <div class="md:ml-5 ml-2 ">
      <p class="hover:text-yellow-400 text-gray-700 md:text-sm text-xs cursor-pointer" @click="openLink(url)">
        {{ text }}
      </p>
    </div>
  </div>
</template>


<script>
export default ({
  props: {
    text: {
      type: String,
      default: null
    },
    date: {
      type: String,
      default: null
    },
    type: {
      type: String,
      default: null
    },
    url: {
      type: String,
      default: null
    }
  },
  methods: {
    openLink (url) {
      window.open(url, '_blank')
    }
  }
})
</script>

<style scoped>
.custom-bg {
  background-color: #51418a;
}
</style>