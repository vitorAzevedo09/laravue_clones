<script setup>
import { toRefs } from 'vue';
import { RouterLink } from 'vue-router';

const props = defineProps({
    image: {
        default: '',
        type: String
    },
    title: {
        default: '',
        type: String
    },
    subTitle: {
        default: '',
        type: String
    }
})

const { image, title, subTitle } = toRefs(props);

</script>
<template>
  <RouterLink to="library">
    <div class="bg-[#111111] p-4 rounded-md m-2 hover:bg-[#252525] cursor-pointer" />
  </RouterLink>
</template>

