<script setup>
    import { ref } from 'vue';
    const contador = ref(0);
    const incrementar = () => {
        contador.value ++;
    }
</script>

<template>
    <button @click="incrementar()" class="btn btn-primary" >Contador {{ contador }}</button>
    
</template>

<style>
</style>