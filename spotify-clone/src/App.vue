<script setup>
import { ref, onMounted } from "vue";
import { RouterView, RouterLink } from "vue-router";
import MenuItem from "./components/MenuItem.vue";
import MusicPlayer from "./components/MusicPlayer.vue";


import { useSongStore } from './stores/song.js'
import { storeToRefs } from 'pinia'
const useSong = useSongStore()

const { isPlaying, currentTrack } = storeToRefs(useSong)

import ChevronUp from "vue-material-design-icons/ChevronUp.vue";
import ChevronDown from "vue-material-design-icons/ChevronDown.vue";
import ChevronRight from "vue-material-design-icons/ChevronRight.vue";
import ChevronLeft from "vue-material-design-icons/ChevronLeft.vue";

onMounted(() => {
  isPlaying = false
})

let openMenu = ref(false);
</script>
<template>
  <div>
    <div class="w-[81%] h-[40px] fixed right-0 z-20 bg-[#101010] bg-opacity-80 flex items-center justify-between">
      <div class="flex items-center ml-6">
        <button
          type="button"
          class="rounded-full bg-black p-[1px] cursor-pointer"
        >
          <ChevronLeft
            fill-color="#FFFFFF"
            :size="30"
          />
        </button>
        <button
          type="button"
          class="rounded-full ml-4 bg-black p-[1px] cursor-pointer"
        >
          <ChevronRight
            fill-color="#FFFFFF"
            :size="30"
          />
        </button>
      </div>
      <button
        class="bg-black hover:bg-[#282828] rounded-full p-0.5 pr-3 mr-8 mt-0.5 cursor-pointer"
        @click="openMenu = !openMenu"
      >
        <div class="flex items-center">
          <img
            class="rounded-full"
            width="27"
            src="https://yt3.ggpht.com/yti/AHyvSCBNVyNt6TRfQo6BsbKQGxw4E7QWb3VXufgDDwB2wg=s88-c-k-c0x00ffffff-no-rj-mo"
          >
          <div class="text-white text-[0.8rem] ml-1.5 font-semibold">
            Vitor Azevedo
          </div>
          <ChevronDown
            v-if="!openMenu"
            fill-color="#FFFFFF"
            :size="25"
          />
          <ChevronUp
            v-else
            fill-color="#FFFFFF"
            :size="25"
          />
        </div>
      </button>
      <span
        v-if="openMenu"
        class="fixed w-[190px] bg-[#282828] shadow-2xl z-50 rounded-sm top-[52px] left-[calc(100%-200px)] p-1 cursor-pointer"
      >
        <ul class="text-gray-200 font-semibold text-[14px]">
          <li class="px-3 py-2.5 hover:bg-[#3E3D3D] border-b border-b-gray-600">
            Profile
          </li>
          <li class="px-3 py-2.5 hover:bg-[#3E3D3D]">Log Out</li>
        </ul>
      </span>
    </div>
    <div
      id="SideNav"
      class="h-[100%] p-6 w-[260px] fixed z-50 bg-black"
    >
      <RouterLink to="/">
        <img
          width="125"
          src="/images/icons/spotify-logo.png"
        >
      </RouterLink>
      <div class="my-8" />
      <ul>
        <RouterLink to="/">
          <MenuItem
            :icon-size="23"
            name="Home"
            icon-string="home"
            page-url="/"
          />
        </RouterLink>
        <RouterLink to="/search">
          <MenuItem
            :icon-size="24"
            name="Search"
            icon-string="search"
            page-url="/search"
          />
        </RouterLink>
        <RouterLink to="/library">
          <MenuItem
            :icon-size="23"
            name="Library"
            icon-string="library"
            page-url="/library"
          />
        </RouterLink>
      </ul>
      <div class="py-3.5" />
      <MenuItem
        :icon-size="24"
        name="Create Playlist"
        icon-string="playlist"
        page-url="/playlist"
      />
      <MenuItem
        :icon-size="27"
        name="Liked Songs"
        icon-string="liked"
        page-url="/liked"
      />
      <div class="border-b border-b-gray-700" />
      <ul>
        <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white cursor-pointer">
          My Playlist #1
        </li>
        <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white cursor-pointer">
          My Playlist #2
        </li>
        <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white cursor-pointer">
          My Playlist #3
        </li>
        <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white cursor-pointer">
          My Playlist #4
        </li>
      </ul>
    </div>
  </div>
  <div class="fixed -right-0 top-0 w-[calc(100%-260px)] overflow-auto h-full bg-gradient-to-b from-[#1C1C1C] to-black">
    <div class="mt-[70px]" />
    <RouterView class="w-[83%] ml-5" />
    <div class="mb-[100px]" />
  </div>

  <MusicPlayer />
</template>
