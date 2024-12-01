<template>
    <div class="card" style="width: 18rem;">
        <img :src="imagen" class="card-img-top" alt="ImgPeli">
        <div class="card-body">
            <h5 class="card-title">{{ titulo }}</h5>
            <p class="card-text">{{ descripcionp }}</p>
            <a href="#"
                class="btn btn-primary"
                @click="$emit('changeNameInCard', titulo)"
            >Arriba</a>
        </div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    titulo: {

        type: String,
        default: 'Titulo por default',
    },
    descripcionp: String,
    imagen: {
        type: String,
        required: true,
    },
  })

  </script>