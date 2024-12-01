<script setup>
import { ref } from 'vue';
import MovieCard from '../users/components/MovieCard.vue';

const data = ref([])

const options = {
  method: 'GET',
  headers: {
    accept: 'application/json',
    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJiOWFlYmZmZmM0ZDAzYTNlZDU5MmMzNmVjZTA5NjA2MiIsIm5iZiI6MTczMDc2MzE5Ny4yNzYzNDA1LCJzdWIiOiI2NzI5MGMxNDJlMWI3OTc4ZGJiM2EzM2UiLCJzY29wZXMiOlsiYXBpX3JlYWQiXSwidmVyc2lvbiI6MX0.Kc8pZT99AjpWOJS16tBz0JdL3THFzK00p99MIERFnEU',
  },
};

const getMovies = async () => {
    try {
        const response = await fetch('https://api.themoviedb.org/3/trending/movie/week?language=es-MX', options);
        const movies = await response.json();
        data.value = movies.results;
    } catch (error) {
        console.error(error);
    } finally {
        
    }
}

const valorPelis = 10;
const inicio = ref(0)
const fin = ref(10)

const nextMovies = () => {
    inicio.value = inicio.value + valorPelis;
    fin.value = fin.value + valorPelis;
}

const backMovies = () => {
    inicio.value = inicio.value - valorPelis;
    fin.value = fin.value - valorPelis;
}

getMovies()
</script>

<template>
    <h5 class="display-5 text-primary">Las Peliculas más Populares de 2024</h5>

    <button class="btn btn-primary me-3" 
        @click="backMovies" 
        :disabled="inicio <= 0 ? true : false"
        >
        Retroceder
    </button>
    
    <button class="btn btn-primary" 
        v-on:click="nextMovies" 
        :disabled="fin >= data.length"
        >
        Avanzar
    </button>

    <hr>

    <div class="row">
        <MovieCard
            v-for="(movie, index) in data.slice(inicio, fin)" 
            :key="movie.id" 
            :titulo="movie.title" 
            :descripcionp="movie.overview" 
            :imagen="'https://image.tmdb.org/t/p/w500' + movie.poster_path" 
            class="col-4 mb-4">
        </MovieCard>
    </div>
</template>
