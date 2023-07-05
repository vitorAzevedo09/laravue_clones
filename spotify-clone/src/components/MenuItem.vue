
<script setup>
import { ref, toRefs, watchEffect } from 'vue';
import useRouter from 'vue-router';

const route = useRouter()

const props = defineProps({
    iconString: String,
    iconSize: Number,
    pageUrl: String,
    name: String,
});

const { iconString, pageUrl, name, iconSize } = toRefs(props);

let icon = ref(null)

let textIsHover = ref(false)
    
    
</script>
<template>
    <div>

    </div>
</template>


<style scoped>

</style>
