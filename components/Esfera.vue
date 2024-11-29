<template>
    <div>
        <input type="number" id="r" placeholder="Raio" v-model="raio">
        <input type="button" value="Calcular" @click="calcular">

        <div>
            <h1>a área é {{ area }}</h1>
            <h1>o volume é {{volume}}</h1>
            <h1>o perimetro é {{perimetro}}</h1>
        </div>   
    </div>
</template>

<script setup lang="ts">

const raio = ref(0)
const area = ref(0)
const volume = ref(0)
const perimetro = ref(0)

const calcular = () => {
    try{
    const data = useFetch('https://localhost:8000/api/esfera',{
        method: 'POST',
        body: JSON.stringify({raio}),
    })

    area = data.volume
    volume = data.area
    perimetro = data.perimetro
    }catch(e){
        console.log(e)
    }
}



</script>

<style lang="scss" scoped>

</style>