<script setup lang="ts">
import { ref, watch } from 'vue'
import IconTooltip from '../icons/IconTooltip.vue'
const isShowPopUp = ref(true)
const newFeatures = ref('')
const isButtonDisabled = ref(true)
const isShowTooltip = ref(false)

watch(newFeatures, async (newValue) => {
  if (newValue) {
    isButtonDisabled.value = false
  } else {
    isButtonDisabled.value = true
  }
})
</script>
<template>
  <div
    class="fixed inset-0 px-2 z-10 overflow-hidden flex items-center justify-center"
    :style="{ display: !isShowPopUp ? 'none' : 'flex' }"
  >
    <div class="absolute inset-0 bg-gray-500 bg-opacity-75 transition-opacity"></div>
    <!-- Modal Content -->
    <div
      class="bg-white rounded-md shadow-xl overflow-hidden max-w-md w-full px-7 py-6 z-50 text-black md:min-w-[580px]"
    >
      <!-- Modal Header -->
      <div class="text-black px-4 py-2 flex justify-between">
        <h2 class="text-4xl font-semibold">New Features Available</h2>
      </div>
      <!-- Modal Body -->
      <div class="p-4 relative">
        <p class="mb-3 text-sm">
          The name of your workspace will be visible to your customers. For us, it is "SAAS First".
          You will NOT be able to change this later.
        </p>
        <div class="text-base mb-2 flex items-center relative">
          <p>New UI/UX Designer</p>
          <IconTooltip
            class="ml-4 cursor-pointer"
            @mouseover="isShowTooltip = true"
            @mouseleave="isShowTooltip = false"
          />
          <div
            :style="{ opacity: isShowTooltip ? '1' : '0' }"
            class="text-xs top-[-55px] left-[42px] max-w-[240px] absolute z-10 inline-block text-[#6C7880] px-3 py-2 font-medium bg-white border border-gray-200 rounded-xl shadow-sm"
          >
            Lorem Ipsum is simply dummy text of the printing…
            <div
              class="bottom-[-8px] shadow-sm absolute border-solid border-t-gray-300 border-t-8 border-x-transparent border-x-8 border-b-0 left-[50%] translate-[-50%,-50%]"
            ></div>
          </div>
        </div>
        <div class="text-base mb-12 flex items-center relative">
          <p>New FE Designer</p>
          <IconTooltip class="ml-4 cursor-pointer" />
        </div>
        <p class="mb-2">Request New Features</p>
        <input
          v-model="newFeatures"
          type="text"
          placeholder="e.g. mobile app developer"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
        />
      </div>
      <!-- Modal Footer -->
      <div class="px-4 py-2 flex gap-4 w-full justify-center">
        <button
          @click="isShowPopUp = false"
          class="py-2 bg-gray-200 font-semibold text-base rounded-md w-full text-black"
        >
          Cancel
        </button>
        <button
          :disabled="isButtonDisabled"
          @click="isShowPopUp = false"
          class="py-2 bg-[#3D22CF] font-semibold text-base text-white rounded-md w-full disabled:opacity-25 focus:outline-none"
        >
          Send
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
