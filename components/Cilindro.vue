<template>
    <div>
        <input type="number" id="raio" placeholder="Raio" v-model="medidasCilindro.raio">
        <input type="number" id="altura" placeholder="Altura" v-model="medidasCilindro.altura">
        <input type="button" value="Calcular" @click="calcular">
    </div>
    <div>
        <h1>a área é {{ area }}</h1>
    </div>
    <div>
        <h1>o volume é {{ volume }}</h1>
    </div>
    <div>
        <h1>o perimetro é {{ perimetro }}</h1>
    </div>
</template>

<script setup lang="ts">

    const medidasCilindro = {
        raio: ref(0),
        altura: ref(0)
    }

    const area = ref(0)
    const volume = ref(0)
    const perimetro = ref(0)

    const calcular = () => {
        try {
            const data = useFetch('https://localhost:8000/api/cilindro', {
                method: 'POST',
                body: JSON.stringify({ medidasCilindro }),
            })

            area = data.area
            volume = data.volume
            perimetro = data.perimetro
        } catch (e) {
            console.log(e)
        }
    }
</script>

<style lang="scss" scoped>

</style>