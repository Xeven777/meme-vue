<script setup>
defineProps({
  data: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <div
    class="card card-compact border border-green-800/40 rounded-xl overflow-hidden bg-base-100 shadow-xl hover:scale-105 transition-all "
  >
    <figure>
      <img :src="data.url" :alt="data.name" />
    </figure>
    <div class="card-body px-3 py-4">
      <p class="text-sm md:text-normal text-zinc-300">
        {{ data.name }}
      </p>
      <div class="card-actions justify-end"></div>
    </div>
  </div>
</template>
