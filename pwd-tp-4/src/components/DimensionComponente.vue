<template>
    <div>
        <h2>Dimensiones del componente</h2>
        <p>Ancho: {{ width }}px</p>
        <p>Alto: {{ height }}px</p>
    </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const width = ref(window.innerWidth);
const height = ref(window.innerHeight);

function actualizarDimensiones() {
    width.value = window.innerWidth;
    height.value = window. innerHeight;
}

onMounted(() => {
    window.addEventListener('resize', actualizarDimensiones);
});

onUnmounted(() => {
    window.removeEventListener('resize', actualizarDimensiones);
});



</script>

<style scoped>

</style>