<template>
    <div>
        <input type="number" id="lado" placeholder="Lado" v-model="lado">
        <input type="button" value="Calcular" @click="calcular">
    </div>
</template>

<script setup lang="ts">

const lado = ref(0)
const area = ref(0)
const volume = ref(0)
const perimetro = ref(0)

const calcular = () => {
    try {
        const data = useFetch('https://localhost:8000/api/cubo', {
            method: 'POST',
            body: JSON.stringify({ lado }),
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