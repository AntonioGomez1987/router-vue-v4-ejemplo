<script setup>

import { useRoute, useRouter } from 'vue-router'
import { useGetData } from '@/composables/getData.js'
import { useFavoritosStore } from '@/store/favoritos.js'

const {data, loading, getData, error} = useGetData()

const route = useRoute();
const router = useRouter();
const useFavoritos = useFavoritosStore();

const {add, findpoke} = useFavoritos;


const back = () => {
    router.push("/pokemons")
}

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
console.log(data);

</script>

<template>
    <p v-if="loading">Cargando informacion...</p>
    <div class="alert alert-danger mt-2" v-if="error">No existe el POKEMON</div>
    <div v-if="data">
        <h1>Pokemon nombre: {{ $route.params.name }}</h1>
        <img :src="data.sprites?.other.dream_world.front_default" alt="">
        <br>
        <img :src="data.sprites?.front_default" alt="">
        <img :src="data.sprites?.back_default" alt="">
        <img :src="data.sprites?.front_shiny" alt="">
        <img :src="data.sprites?.back_shiny" alt="">        
        <br>
        <button 
            :disabled="findpoke(data.name)" 
            class="btn btn-primary mb-2" 
            @click="add(data)"
            >
            Agregar a Favoritos
        </button>
    </div>
    <button @click="back" class="btn btn-outline-primary">Volver</button>
</template>                                                                                                                                                                                                 