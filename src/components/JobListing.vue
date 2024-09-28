<script setup>
import { ref, computed, defineProps } from 'vue';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faLocationDot } from '@fortawesome/free-solid-svg-icons'

const props = defineProps({
  job: Object,
  required: true
})

const showFullDescription = ref(false)

const toggleDescription = () => {
  showFullDescription.value = !showFullDescription.value
}

const truncatedDescription = computed(() => {
  const { description } = props.job
  if (showFullDescription.value || description.length < 90) {
    return description
  } else {
    return description.substring(0, 90) + '...' + description.length
  }
})
</script>

<template>
<div class="bg-white rounded-xl shadow-md relative">
  <div class="p-4">
    <div class="mb-6">
      <div class="text-gray-600 my-2">{{ job.type }}</div>
      <h3 class="text-xl font-bold">{{ job.title }}</h3>
    </div>

    <div class="mb-5">
      <span>
        {{ truncatedDescription }}
      </span><br>
      <a href="#" class="text-green-500" @click.prevent="toggleDescription" v-if="truncatedDescription.length > 90">
        {{ showFullDescription ? ' less' : ' more' }}
      </a>
    </div>

    <h3 class="text-green-500 mb-2">{{ job.salary }} / Year</h3>

    <div class="border border-gray-100 mb-5"></div>

    <div class="flex flex-col lg:flex-row justify-between mb-4">
      <div class="text-orange-700 mb-3">
        <FontAwesomeIcon :icon="faLocationDot" class="text-lg" />
        {{ job.location }}
      </div>
      <RouterLink
        :to="`jobs/${job.id}`"
        class="h-[36px] bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-center text-sm"
      >
        Read More
      </RouterLink>
    </div>
  </div>
</div>
</template>