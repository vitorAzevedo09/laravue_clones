<script setup>
import CategorySelect from '@/components/CategorySelect.vue'
</script>
<template>
  <div
    class="pb-8"
  >
    <button
      type="button"
      class="w-80 text-white text-xl font-semibold hover:underline cursor-pointer"
    >
      Podcasts to make you smarter
    </button>
    <div class="py-1.5" />
    <div class="ml-10 grid xl:grid-cols-5 lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-2 gap-6">
      <CategorySelect
        category="Podcasts"
        image="https://picsum.photos/id/112/300/300"
      />
      <CategorySelect
        category="Audiobooks"
        image="https://picsum.photos/id/113/300/300"
      />
      <CategorySelect
        category="Made for you"
        image="https://picsum.photos/id/114/300/300"
      />
      <CategorySelect
        category="New Release"
        image="https://picsum.photos/id/115/300/300"
      />
      <CategorySelect
        category="What happen"
        image="https://picsum.photos/id/116/300/300"
      />
      <CategorySelect
        category="Journal"
        image="https://picsum.photos/id/117/300/300"
      />
      <CategorySelect
        category="Daily Mix"
        image="https://picsum.photos/id/121/300/300"
      />
    </div>
  </div>
</template>
