
<script setup>

import { useRouter,useRoute } from 'vue-router'
import { useGetData } from '@/composables/getData.js'

const { getData } = useGetData()

const router = useRouter();
const route = useRoute();

const back = () => {
    router.push("/")
}

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
</script>

<template>
    <h1>404</h1>
    <button @click="back" class="btn btn-outline-primary">Volver</button>
</template>