<script setup>
//defineProps(['titulo', 'id', 'contenido'])

defineProps({
    titulo: String,
    id : Number,
    contenido :{
        type : String, 
        default : 'Sin descripcion'
    }
})

</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{ id }}  -    {{ titulo }}</h5>
            <p>{{ contenido }}</p>
        </div>
    </div>
</template>

<style></style>