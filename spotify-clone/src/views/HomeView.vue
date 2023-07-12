<script setup>
import { ref } from 'vue';
import HomeCard from '../components/HomeCard.vue';

const recommendations = ref([{
  title: "Podcasts to make you smarter",
  homeCards: [
    {
      image: "https://picsum.photos/id/30/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    },
    {
      image: "https://picsum.photos/id/45/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    },
    {
      image: "https://picsum.photos/id/60/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    },
    {
      image: "https://picsum.photos/id/75/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    },
    {
      image: "https://picsum.photos/id/100/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    }
  ]
},
{

  title: "Recommended songs",
  homeCards: [
    {
      image: "https://picsum.photos/id/31/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    },
    {
      image: "https://picsum.photos/id/46/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    },
    {
      image: "https://picsum.photos/id/61/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    },
    {
      image: "https://picsum.photos/id/76/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    },
    {
      image: "https://picsum.photos/id/101/300/300",
      title: "Title here",
      subtitle: "Subtitle here"
    }
  ]
}
])

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
