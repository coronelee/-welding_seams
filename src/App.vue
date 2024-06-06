 
<script setup>
  import { ref } from 'vue';
  import HelpComponent from './components/HelpComponent.vue';
  const imageSrc = ref(null);
  const height = ref('33%')
  const page = ref(null)
  const image = ref('/picture/butt.png')

  const editImage = (img) => {
     image.value = img
  }

  const onFileChange = (event) => {
    const selectedFile = event.target.files[0];
    imageSrc.value = URL.createObjectURL(selectedFile);
  } 

  const downloadImage = (id) => {
    document.getElementById(""+id).click();
    height.value = '100%'
    page.value = "image"
  }
   
const openQuePage = () => {
  height.value = '66%'
  page.value = "que"
}

</script>
<template>
<input type="file" id="file" class="hidden" @change="onFileChange">
<input type="file" id="camera" accept="image/*" capture="camera" class="hidden" @change="onFileChange">

  <div class="w-screen h-screen bg-[#19173d] flex flex-col justify-end items-end">
    <div v-if="page === 'que'" class="w-full h-[33%] flex justify-center items-center p-8">
    <img :src="image"  alt="" class="w-full ">

    </div>
    <div :style="`height:` + height"  class="bg-[#252350] w-full transition-all duration-1000  border-t border-[#393677] rounded-t flex justify-center items-center flex gap-8 flex-col p-8
                [&>button]:text-white [&>button]:text-2xl [&>button]:p-2 [&>button]:rounded-xl [&>button]:border [&>button]:border-[#393677] [&>button]:px-4 [&>button]:py-2 [&>button]:bg-[#252350]">
          <button v-if="!imageSrc" @click="downloadImage('file')">Загрузить фотографию</button>
          <button v-if="!imageSrc" @click="downloadImage('camera')">Сделать фотографию</button>

          <div v-if="imageSrc" class="w-full h-full flex flex-col justify-center items-center relative gap-12">
          
          <img v-if="page == 'image'" :src="imageSrc" class="  " alt="Uploaded Image">

          <component v-if="page === 'que'" :is="HelpComponent" :editImage="editImage"/>
          <div class="w-full h-20 flex justify-between absolute bottom-0 [&>div>button]:rounded-full [&>div>button]:bg-[#252350] [&>div>button]:w-20 [&>div>button]:h-20 [&>div>span]:text-white">
            <div class="flex flex-col justify-between items-center ">
              <button @click="downloadImage('file')" class="bg-[url('/svg/download.svg')] bg-contain bg-center bg-no-repeat"></button>
              <span>Загрузить</span>
            </div>
            <div class="flex flex-col justify-between items-center ">
              <button @click="openQuePage" class="bg-[url('/svg/que.svg')] bg-contain bg-center bg-no-repeat"></button>
              <span>Помощь</span>
            </div>
            <!-- <div class="flex flex-col justify-between items-center ">
              <button @click="downloadImage('file')" class="bg-[url('/svg/download.svg')] bg-contain bg-center bg-no-repeat"></button>
              <span>zxc</span>
            </div>
            <div class="flex flex-col justify-between items-center ">
              <button @click="downloadImage('file')" class="bg-[url('/svg/download.svg')] bg-contain bg-center bg-no-repeat"></button>
              <span>zxc</span>
            </div> -->
          </div>
        </div>
    </div>

    
  
  </div>
</template>

 