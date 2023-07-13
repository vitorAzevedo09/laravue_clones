<script setup>
import { ref } from 'vue'
import CategorySelect from '@/components/CategorySelect.vue'
import categories_json from '@/json/categories.json'

const categories = ref(categories_json)

</script>
<template>
  <div class="pb-8">
    <button
      type="button"
      class="w-100 ml-2 text-white text-xl font-semibold hover:underline cursor-pointer"
    >
      Browse All
    </button>
    <div class="py-1.5" />
    <div class="mr-5 ml-5 grid xl:grid-cols-5 lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-2 gap-6">
      <CategorySelect
        v-for="(category, index) in categories"
        :key="index"
        :category="category.category"
        :image="`https://picsum.photos/id/${31 + index}/300/300`"
      />
    </div>
  </div>
</template>
