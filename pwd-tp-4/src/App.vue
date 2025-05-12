<template>
  <div>
    <h1>Componentes</h1>
    <div>
      <button @click="componenteSeleccionado = 'Lista'">Lista</button>
      <button @click="componenteSeleccionado = 'Tareas'">Tareas</button>
      <button @click="componenteSeleccionado = 'DimensionComponente'">Dimensiones</button>
    </div>
    <component :is="componentes[componenteSeleccionado]" />
  </div>  
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Lista from './components/Lista.vue';
import Tareas from './components/Tareas.vue';
import DimensionComponente from './components/DimensionComponente.vue';


const componenteSeleccionado = ref('Lista');

const componentes = {
  Lista,
  Tareas,
  DimensionComponente
};


</script>

<style scoped>
button{
  margin-right: 10px;
}

</style>
