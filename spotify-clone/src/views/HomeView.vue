<script setup>
import { ref } from 'vue';
import HomeCard from '../components/HomeCard.vue';
import recommendations_json from '../json/recommentations.json'

const recommendations = ref(recommendations_json)

</script>

<template>
  <div
    v-for="recommendation, i in recommendations"
    :key="i"
    class="pb-8"
  >
    <button
      type="button"
      class="w-80 text-white text-xl font-semibold hover:underline cursor-pointer"
    >
      {{ recommendation.title }}
    </button>
    <div class="py-1.5" />
    <div class="flex items-center">
      <HomeCard
        v-for="homeCard, j in recommendation.homeCards"
        :key="j"
        :image="homeCard.image"
        :title="homeCard.title"
        :subtitle="homeCard.subtitle"
      />
    </div>
  </div>
</template>
