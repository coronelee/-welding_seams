<script setup>
import { ref } from 'vue';

const imageSrc = ref("");
const onFileChange = (event) => {
  const selectedFile = event.target.files[0];
  imageSrc.value = URL.createObjectURL(selectedFile);
}
</script>
<template>
  <div class="w-screen bg-gray-500 h-screen flex flex-col justify-end items-center">
    <div class="w-[90%] h-[90%] bg-gray-100" id="image"><img class="w-full h-full" v-if="imageSrc" :src="imageSrc" alt="Uploaded Image"></div>
    <div class="[&>button]:w-12 [&>button]:h-12 [&>button]:bg-gray-100 [&>button]:text-white [&>button]:m-2 [&>button]:rounded-[50%]"> 
      <button class="bg-[url('/src/assets/svg/download.svg')] bg-no-repeat bg-center bg-contain"><input type="file"  class="opacity-0 w-12 h-full" size="1024" @change="onFileChange"></button>
      <button></button><button></button><button></button> 
    </div>
  </div>
</template>


