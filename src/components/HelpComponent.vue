<script setup>
const props = defineProps({
    editImage: Function
})
import { ref } from 'vue';

const editImg = (img) => {
    props.editImage(img)
}


const count = ref(2)
const arr = 
    [
        {   
            id: 0,
            name:'Стыковой шов',
            img: '/picture/butt.png',
            discription: 'Наиболее распространенный метод сварки, который используется для соединения листов металла и торцевых частей труб. Требованием к стыковым швам является жесткое соединение двух заготовок с допустимым зазором величиной не более 2 мм, заполняемым расплавленным металлом, образующимся при плавлении электрода.'
        },
        {
            id: 1,
            name: 'Угловой шов',
            img: '/picture/angular.jpg',

            discription:'Этот вид соединения довольно сложен в исполнении, так как в процессе сварки расплавленный металл имеет свойство стекать с угловой поверхности – с вертикальной части заготовки на горизонтальную. Чтобы справиться с такой проблемой, сварщику необходимо держать электрод под правильным углом наклона.'
        },
        {
            id: 2,
            name: 'Тавровый шов',
            img: '/picture/tavrovoe.jpg',
            discription:'Если выполнить разрез такого соединения, то можно увидеть, что одна деталь стыкуется с другой по профилю, выполненным в виде буквы «Т». По ГОСТу существует 9 видов исполнения тавровых швов, для которых требуется глубокое проплавление, выполняемое путем применения автоматического вида сварки.'
        }
    ]
</script>




<template>
    <div class="h-3/4 w-full  absolute top-0 flex flex-col">
        <span class="text-3xl text-white">{{ arr[count].name }}</span>
        <span class="text-xl text-[#abaeb5] mt-4">{{ arr[count].discription }}</span>
    </div>
    <div class="h-[15px] w-full  absolute bottom-24 flex justify-center items-center [&>img]:w-[45px] [&>img]:h-[45px]  [&>div]:w-[15px] [&>div]:h-[15px] [&>div]:rounded-full   [&>div]:border [&>div]:border-[#393677] [&>div]:m-2 [&>div]:bg-[#252350]">
        <img src="/svg/left.svg" alt="" @click="count = count - 1 < 0 ? 2 : count - 1, editImg(arr[count].img)">
        <div :style="count == 0 ? 'background-color: #393677' : ''"></div>
        <div :style="count == 1 ? 'background-color: #393677' : ''"></div>
        <div :style="count == 2 ? 'background-color: #393677' : ''"></div>
        <img src="/svg/right.svg" alt="" @click="count = count + 1 > 2 ? 0 : count + 1, editImg(arr[count].img)">

    </div>
</template>