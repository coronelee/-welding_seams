<!-- <script setup>
import { ref } from 'vue';

const imageSrc = ref("");
const onFileChange = (event) => {
  const selectedFile = event.target.files[0];
  imageSrc.value = URL.createObjectURL(selectedFile);
}
</script> -->
<script setup>
  import { ref } from 'vue';
 
  const imageSrc = ref("");
 
  
  const onFileChange = (event) => {
    const selectedFile = event.target.files[0];
    imageSrc.value = URL.createObjectURL(selectedFile);
    console.log(imageSrc.value)
  } 

  const downloadImage = () => {
    document.getElementById('file').click();
  }
</script>
<template>
<input type="file" id="file" class="hidden" @change="onFileChange">
<input type="file" id="camera" accept="image/*" capture="camera" class="hidden" @change="onFileChange">

  <div class="w-screen h-screen bg-gray-500 ">
    <div v-if="!imageSrc" class="w-full h-full flex flex-col justify-center items-center text-white [&>div]:border [&>div]:border-gray-300 [&>div]:p-2 [&>div]:m-2 [&>div]:rounded-xl [&>div]:bg-gray-600">
      <div onclick=" document.getElementById('camera').click(); ">Сделать снимок</div>
      <div @click="downloadImage">Загрузить картинку</div>
    
      
    </div>
    <div v-if="imageSrc" class="w-full h-full p-8 flex flex-col justify-center items-center">
      <div class="w-[90%] h-[90%] bg-gray-100" >
        <img class="w-full h-full " v-if="imageSrc" :src="imageSrc" alt="Uploaded Image">
      </div>
      <div class="[&>button]:w-12 [&>button]:h-12 [&>button]:bg-gray-100 [&>button]:text-white [&>button]:m-2 [&>button]:rounded-[50%] [&>button]:bg-center [&>button]:bg-no-repeat [&>button]:bg-contain">
        <button @click="downloadImage" class="bg-[url('src/assets/svg/download.svg')] "></button ><button class="bg-[url('src/assets/svg/que.svg')] "></button><button></button><button></button>
      </div>
    </div>
  </div>
</template>


