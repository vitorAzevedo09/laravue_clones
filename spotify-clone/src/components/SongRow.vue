<script setup>
import { ref, toRefs, onMounted } from 'vue'
import Heart from 'vue-material-design-icons/Heart.vue'
import Play from 'vue-material-design-icons/Play.vue'
import Pause from 'vue-material-design-icons/Pause.vue'

const isHover = ref(false)
let isTrackTime = ref(null)

const props = defineProps({
  track: {
    default: () => { },
    type: Object
  },
  artist: {
    default: () => { },
    type: Object
  },
  index: {
    default: 0,
    type: Number
  }
});

const { track, artist, index } = toRefs(props)

onMounted(() => {
  const audio = new Audio(track.value.path);
  audio.addEventListener('loadedmetadata', () => {
    const duration = audio.duration;
    const minutes = Math.floor(duration / 60);
    const seconds = Math.floor(duration % 60);

    isTrackTime.value = minutes + ':' + seconds.toString().padStart(2, '0')
  })
})

</script>
<template>
  <li
    class="flex items-center justify-between rounded-md hover:bg-[#2A2929]"
    @mouseenter="isHover = true"
    @mouseleave="isHover = false"
  >
    <div class="flex items-center w-full py-1.5">
      <div
        v-if="isHover"
        class="w-[40px] ml-[14px] mr-[6px] cursor-pointer"
      >
        <Play
          v-if="true"
          fill-color="#FFFFFF"
          :size="25"
        />
        <Pause
          v-else
          fill-color="#FFFFFF"
          :size="25"
        />
      </div>
      <div
        v-else
        class="text-white font-semibold w-[40px] ml-5"
      >
        {{ index }}
      </div>
      <div>
        <div class="text-white font-semibold">
          {{ track.name }}
        </div>
        <div class="text-sm font-semibold text-gray-400">
          {{ artist.name }}
        </div>
      </div>
    </div>
    <div class="flex items-center mr-5">
      <button
        type="button"
        v-if="isHover"
      >
        <Heart
          fill-color="#1BD760"
          :size="22"
        />
      </button>
      <div
        v-if="isTrackTime"
        class="text-xs mx-5 text-gray-400"
      >
        {{ isTrackTime }}
      </div>
    </div>
  </li>
</template>