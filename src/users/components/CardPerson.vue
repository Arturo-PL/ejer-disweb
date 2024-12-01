<template>
    <div class="card" style="width: 18rem;">
        <img :src="imagen" class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title">{{  titulo }}</h5>
            <p class="card-text">{{ descripcionp  }}</p>
            <a href="#" 
                class="btn btn-primary"
                @:click ="$emit('changeNameInCard', titulo  )"
            >Seleccionar</a>
        </div>
    </div>
    
</template>
<script setup>
//defineProps(['titulo','descripcionp'])

defineProps({
    titulo: {
        typeof: String,
        default: 'Titulo por default'
    },
    descripcionp: String,
    imagen: {
        typeof: String,
        required: true
    },
    
})

</script>
