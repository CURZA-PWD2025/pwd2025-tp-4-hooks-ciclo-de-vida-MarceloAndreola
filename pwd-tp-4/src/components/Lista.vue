<template>
    <div>
        <h1>Lista vuejs </h1>
        <input type="text" v-model="texto" placeholder="texto" @keyup.enter="agregarTarea">
        <ul>
            <li 
            v-for="(tarea, index) in tareas" 
            :key="index"
            :style="{ color: textoColor }"
            >
                {{ tarea }}
            </li>
        </ul>
        <p>{{ texto }}</p>
        <button @click="agregarTarea">agregar</button>
        <button @click="limpiarLista">limpiar</button>
        <br>
    </div>
</template>
  
<script setup lang="ts">
import { ref, onUpdated, onBeforeUpdate, onMounted} from 'vue';

const texto = ref('');
const tareas = ref<string[]>([]);
const textoColor = ref('black');

onMounted(() => {
  setTimeout(() => {
    tareas.value = ['Tarea 1', 'Tarea 2', 'Tarea 3'];
    console.log('Tareas cargadas automáticamente');
  }, 3000);
});


function agregarTarea() {
    if (texto.value) {
        tareas.value.push(texto.value);
        texto.value= '';
    }
}

function limpiarLista() {
    tareas.value = []
}

onBeforeUpdate(() => {
    console.log('Lista aun no modificada')
    textoColor.value = 'green';
});

onUpdated(() => {
  console.log('Lista modificada:', document.querySelectorAll('li').length);
});

</script>
  
<style scoped>  

    ul{
        padding: 0;
    }

    li{
        list-style-type: none;
    }

    button{
        margin-right: 10px;
    }

</style>
  