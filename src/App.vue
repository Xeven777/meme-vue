<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'
import ImgCards from './components/ImgCards.vue'
import AnishTag from './components/AnishTag.vue';

const data = ref(null)
const count = 24

onMounted(async () => {
  try {
    const response = await axios.get(`https://meme-api.com/gimme/${count}`)
    if (response.status !== 200) throw new Error('Oops.Server error')
    data.value = response.data.memes
    console.log(data.value)
  } catch (error) {
    console.error(error)
    alert('Oops.Server error')
  }
})
</script>

<template>
  <main class="w-full h-full max-w-7xl py-4 px-3 flex flex-col items-center justify-center mx-auto">
    <AnishTag />
    <div class="flex">
      <img src="./assets/logo.svg" alt="" class="md:w-16 w-10" />
      <h2 class="text-4xl md:text-7xl pt-2 font-bold -translate-x-2">ueMemes</h2>
    </div>
    <h4 class="text-md md:text-2xl text-center px-6 pt-2 pb-4 tracking-wider text-slate-300">
      24 fresh Memes Templates to make your day!
    </h4>
    <section
      class="md:columns-4 columns-2 break-inside-avoid-column gap-6 mt-2 py-3"
    >
      <ImgCards v-for="(item, index) in data" :key="index" :data="item" />
    </section>
  </main>
</template>

<style scoped>
h2 {
  text-shadow: 0 0 15px rgba(165, 194, 170, 0.308);
}
</style>
