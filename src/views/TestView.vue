<script setup>
import { ref, computed } from 'vue';

const count = ref(2)
const myHtml = ref('<h1>Vue 3 </h1>')
const items = ref([1,2,3,4,5,6])

const evenItem = computed(() => {
  return items.value.filter(i => i % 2 === 0)
})

</script>
<style>
  [v-cloak] {
    display: none;
  }
</style>
<template>
  <div v-cloak class="container mx-auto max-w-[90%]">
    <h2 class="text-2xl font-bold mt-4 mb-2">
      Test
    </h2>
    <div v-for="(item, i) in evenItem" @click="items.splice(i, 1)" :key="item">
      {{ item }}
      <input type="text" class="border p-2 m-1"  @click.stop>
    </div>
  </div>
</template>