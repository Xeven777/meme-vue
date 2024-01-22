<script setup>
import { saveAs } from 'file-saver'

defineProps({
  data: {
    type: Object,
    required: true
  }
})

const downloadImage = (imageUrl) => {
  saveAs(imageUrl, 'VueMeme.jpg')
}
</script>

<template>
  <div
    class="card mb-4 card-compact border border-green-800/40 rounded-xl overflow-hidden bg-base-100 shadow-lg hover:shadow-green-400/30 transition-all"
  >
    <figure class="border-b border-b-green-700/50">
      <img
        loading="lazy"
        :src="data.url"
        :alt="data.title"
        class="transition-all w-full hover:scale-105"
      />
    </figure>
    <div class="card-body px-3 py-4">
      <p class="text-sm md:text-normal text-zinc-300">
        {{ data.title }}
      </p>
      <div class="card-actions justify-end">
        <button
          @click="() => downloadImage(data.url)"
          class="btn btn-sm btn-circle btn-outline btn-primary text-sm"
        >
          <img src="../assets/download.svg" alt="Download" />
        </button>
        <a :href="data.postLink" target="_blank" rel="noopener noreferrer">
          <button class="btn btn-sm btn-success text-sm">Visit</button>
        </a>
      </div>
    </div>
  </div>
</template>
