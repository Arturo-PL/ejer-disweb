<template>
    <h2 class="display-4"> Persona: {{ nombreActual }}</h2>
  
    <CardPerson v-for="p in listPersons" :key="p.nombre" 
      class="me-2 mt-2" 
      :titulo="p.nombre"
      :descripcionp="p.descripcion" 
      :imagen="p.foto"
      @changeNameInCard="handleChangeName"
    >
    </CardPerson>
  
  
  </template>
  
  
  <script setup>
  import { ref } from 'vue';
  import CardPerson from './components/CardPerson.vue';
  defineProps({
    listPersons: Array
  })
  
  const nombreActual = ref('No name')
  
  const handleChangeName = (newName) => {
    nombreActual.value = newName
  }
  
  
  </script>
  