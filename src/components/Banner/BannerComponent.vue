<script setup lang="ts">
import { ref } from 'vue'
import PopupComponent from '../Popup/PopupComponent.vue';
const isShowBanner = ref(false)
const isShowPopUp = ref(false)
setTimeout(() => {
  isShowBanner.value = true
}, 10000)

function showPopup() {
  isShowBanner.value = false
  isShowPopUp.value = true
}

</script>

<template>
  <div
    class="absolute  top-0 w-full banner-container flex items-center justify-center"
    :style="{ display: !isShowBanner ? 'none' : 'flex' }"
  >
    <img src="../../assets/image-banner.png" class="mr-[53px]" />
    <div class="flex flex-col items-start gap-3">
      <p class="font-extrabold text-4xl text-white">New features available!</p>
      <p class="text-base text-white">
        Lorem Ipsum is simply dummy text of the printing and typesetting industry.
      </p>
      <button
        class="font-semibold text-base text-white py-3 min-w-[200px] bg-[#67C7D0] view-feature-button rounded-xl hover:bg-sky-600"
        @click="showPopup()"
        data-modal-target="authentication-modal" data-modal-toggle="authentication-modal"
      >
        View New Features
      </button>
      <div class="absolute top-3 right-6 text-xl cursor-pointer" @click="isShowBanner = false">x</div>
    </div>
  </div>
  <template v-if="isShowPopUp">
    <PopupComponent />
  </template>
</template>

<style scoped>
.banner-container {
  background-image: url('../../assets/background-banner.png');
  background-repeat: no-repeat;
  background-size: cover;
  max-height: 259px;
}
</style>
