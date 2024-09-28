<script setup>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { faCircleArrowLeft } from '@fortawesome/free-solid-svg-icons';
</script>

<template>
  <section>
    <div class="container m-auto py-6 px-6">
      <RouterLink
        to="/jobs"
        class="text-green-500 hover:text-green-600 flex items-center"
      >
        <FontAwesomeIcon :icon="faCircleArrowLeft" class="mr-2" />
        Back to Job Listings
      </RouterLink>
    </div>
  </section>
</template>