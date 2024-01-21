<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'
import ImgCards from './components/ImgCards.vue'

const data = ref(null)

onMounted(async () => {
  try {
    const response = await axios.get('https://api.imgflip.com/get_memes')
    if (response.status !== 200) throw new Error('Oops.Server error')
    data.value = response.data.data.memes
    console.log(data.value)
  } catch (error) {
    console.error(error)
    alert('Oops.Server error')
  }
})
</script>

<template>
  <main class="w-full h-full max-w-7xl py-4 px-3 flex flex-col items-center justify-center mx-auto">
    <h2 class="text-4xl md:text-7xl pt-1 font-bold">VueMemes</h2>
    <h4 class="text-md md:text-2xl py-4 tracking-wider">
      100 fresh Memes Templates to make your day!
    </h4>
    <section class="grid grid-cols-2 sm:grid-cols-3 gap-2 md:grid-cols-4 lg:grid-cols-5 py-3">
      <ImgCards v-for="(item, index) in data" :key="index" :data="item" />
    </section>
  </main>
</template>

<style scoped>
h2 {
  text-shadow: 0 0 15px rgba(165, 194, 170, 0.308);
}
</style>
