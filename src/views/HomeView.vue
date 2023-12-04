<script setup>

import { onMounted } from 'vue';
import { ref, computed } from 'vue';
import dayjs from 'dayjs' // ES 2015
import 'dayjs/locale/es'; // Importa el idioma español

dayjs.locale('es');



const info = ref('');

async function fetchData() {
  try {
    const response = await fetch('https://sitmotul.com.mx/api/statusEval')
    const data = await response.json();
    info.value = data
    // isLoading.value = false
    console.log(info.value);
    // document.getElementById('per').textContent = info.value['periodo'];
  } catch (error) {
    console.error('Error al obtener datos:', error);
  }
}
onMounted(() => {
  fetchData();
})

const fechain = computed(() => {
  return dayjs(info.value.inicio).format('dddd, DD [de] MMMM [del] YYYY');
});

const fechafi = computed(() => {
  return dayjs(info.value.fin).format('dddd, DD [de] MMMM [del] YYYY');
});
</script>



<template>
  <div class="w-full flex flex-col gap-y-5 text">
    <div class="w-full flex flex-row ">

      <div class="w-1/2 flex flex-col gap-y-3 place-items-center">
        <svg xmlns="http://www.w3.org/2000/svg" class="w-20 h-20" viewBox="0 0 256 256">
          <path fill="currentColor"
            d="m225.9 58.31l-96-32a6 6 0 0 0-3.8 0l-96 32A6 6 0 0 0 26 64v80a6 6 0 0 0 12 0V72.32l38.68 12.9A62 62 0 0 0 99 174.75c-19.25 6.53-36 19.59-48 38a6 6 0 0 0 10 6.53C76.47 195.59 100.88 182 128 182s51.53 13.59 67 37.28a6 6 0 0 0 10-6.56c-12-18.38-28.73-31.44-48-38a62 62 0 0 0 22.27-89.53l46.63-15.5a6 6 0 0 0 0-11.38ZM178 120a50 50 0 1 1-89.37-30.8l37.47 12.49a6 6 0 0 0 3.8 0l37.47-12.49A49.78 49.78 0 0 1 178 120Zm-50-30.32L51 64l77-25.68L205 64Z" />
        </svg>

        <div class=" w-full flex flex-col gap-y-1 text">
          <div class="text2">
          <h1 class="text-center" border:7 >Cantidad total de alumnos:</h1>
          <h2 class="text-center">{{ info.alTotal }}</h2>
          </div>
        </div>
      </div>

      <div class="w-1/2 flex flex-col gap-y-3 place-items-center ">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
          class="w-20 h-20">
          <path stroke-linecap="round" stroke-linejoin="round"
            d="M11.35 3.836c-.065.21-.1.433-.1.664 0 .414.336.75.75.75h4.5a.75.75 0 00.75-.75 2.25 2.25 0 00-.1-.664m-5.8 0A2.251 2.251 0 0113.5 2.25H15c1.012 0 1.867.668 2.15 1.586m-5.8 0c-.376.023-.75.05-1.124.08C9.095 4.01 8.25 4.973 8.25 6.108V8.25m8.9-4.414c.376.023.75.05 1.124.08 1.131.094 1.976 1.057 1.976 2.192V16.5A2.25 2.25 0 0118 18.75h-2.25m-7.5-10.5H4.875c-.621 0-1.125.504-1.125 1.125v11.25c0 .621.504 1.125 1.125 1.125h9.75c.621 0 1.125-.504 1.125-1.125V18.75m-7.5-10.5h6.375c.621 0 1.125.504 1.125 1.125v9.375m-8.25-3l1.5 1.5 3-3.75">
          </path>
        </svg>

        <div class=" w-full flex flex-col gap-y-1">
          <h1 class="text-center">Cantidad de evaluaciones finalizadas:</h1>
          <h2 class="text-center">{{ info.alEvaluados }}</h2>
        </div>
      </div>

    </div>

    <div class="w-full flex flex-row gap-x-5 ">
      <div class="w-1/2 flex flex-col gap-y-3 place-items-center ">
        <svg xmlns="http://www.w3.org/2000/svg" width="70" height="70" fill="#000000" viewBox="0 0 256 256">
          <path
            d="M208,32H184V24a8,8,0,0,0-16,0v8H88V24a8,8,0,0,0-16,0v8H48A16,16,0,0,0,32,48V208a16,16,0,0,0,16,16H208a16,16,0,0,0,16-16V48A16,16,0,0,0,208,32ZM72,48v8a8,8,0,0,0,16,0V48h80v8a8,8,0,0,0,16,0V48h24V80H48V48ZM208,208H48V96H208V208Z">
          </path>
        </svg>
        <div class=" w-full flex flex-col gap-y-1 place-items-center">
          <h1 class="text-center">Fecha de inicio:</h1>
          <h2 class="text-center">{{ fechain }}</h2>
        </div>
      </div>


      <div class="w-1/2 flex flex-col gap-y-3 place-items-center ">
        <svg xmlns="http://www.w3.org/2000/svg" width="70" height="70" fill="#000000" viewBox="0 0 256 256">
          <path
            d="M208,32H184V24a8,8,0,0,0-16,0v8H88V24a8,8,0,0,0-16,0v8H48A16,16,0,0,0,32,48V208a16,16,0,0,0,16,16H208a16,16,0,0,0,16-16V48A16,16,0,0,0,208,32ZM72,48v8a8,8,0,0,0,16,0V48h80v8a8,8,0,0,0,16,0V48h24V80H48V48ZM208,208H48V96H208V208Zm-38.34-85.66a8,8,0,0,1,0,11.32l-48,48a8,8,0,0,1-11.32,0l-24-24a8,8,0,0,1,11.32-11.32L116,164.69l42.34-42.35A8,8,0,0,1,169.66,122.34Z">
          </path>
        </svg>
        <div class=" w-full flex flex-col gap-y-1 place-items-center ">
          <h1 class="text-center">Fecha de finalización:</h1>
          <h2 class="text-center">{{ fechafi }}</h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PhStudentLight'
}
</script>