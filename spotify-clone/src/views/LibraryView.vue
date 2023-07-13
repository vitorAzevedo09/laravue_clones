<script setup>
import SongRow from '@/components/SongRow.vue'
import Play from 'vue-material-design-icons/Play.vue'
import DotsHorizontal from 'vue-material-design-icons/DotsHorizontal.vue'
import Heart from 'vue-material-design-icons/Heart.vue'
import ClockTimeThreeOutline from 'vue-material-design-icons/ClockTimeThreeOutline.vue'
import artists from '../json/artists.json'
import { ref } from 'vue'

const artist = ref(artists)

</script>
<template>
  <div class="pb-8">
    <button
      type="button"
      class="w-100 text-white text-xl font-semibold hover:underline cursor-pointer"
    >
      {{ artist.name }}
    </button>
    <div class="py-1.5" />
    <div class="flex items-center w-full relative h-full">
      <img
        width="140"
        :src="artist.albumCover"
      >
      <div class="w-full ml-5">
        <div class="text-white absolute w-full hover:underline cursor-pointer top-0 font-semibold text-lg">
          {{ artist.name }}
        </div>
        <div class="text-gray-300 text-xs flex">
          <div class="flex">
            Album
          </div>
          <div class="ml-2 flex">
            <div class="circle mt-2 mr-2" />
            <span>{{ artist.releaseYear }}</span>
          </div>
          <div class="ml-2 flex">
            <div class="circle mt-2 mr-2" />
            <span>{{ artist.tracks.length }} songs</span>
          </div>
          <div class="absolute flex gap-4 items-center justify-start bottom-0 mb-1.5">
            <button
              type="button"
              class="p-1 rounded-full bg-white"
            >
              <Play
                v-if="true"
                fill-color="#181818"
                size="25"
              />
              <Play
                v-else
                fill-color="#181818"
                size="25"
              />
            </button>
            <button type="button">
              <Heart
                fill-color="#1BD760"
                :size="30"
              />
            </button>
            <button type="button">
              <DotsHorizontal
                fill-color="#FFFFFF"
                :size="25"
              />
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="mt-6" />
    <div class="flex items-center justify-between pc-5 pt-2 mr-5">
      <div class="flex items-center justify-between text-gray-400">
        <div class="mr-7">
          #
        </div>
        <div class="text-sm">
          Title
        </div>
      </div>
      <div>
        <ClockTimeThreeOutline
          fill-color="#FFFFFF"
          :size="18"
        />
      </div>
    </div>
    <div class="border-b border-b-[#2A2A2A] mt-2 mr-3" />
    <div class="mb-4" />
    <ul
      class="w-full"
      v-for="(track, index) in artist.tracks"
      :key="index"
    >
      <SongRow
        :artist="artist"
        :track="track"
        :index="++index"
      />
    </ul>
  </div>
</template>
<style scoped>
.circle {
  width: 4px;
  height: 4px;
  background-color: rgb(189, 189, 189);
  border-radius: 100%;
}
</style>
