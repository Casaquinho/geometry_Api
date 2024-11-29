<template>
    <div class="prisma">
        <input type="number" id="lado1" placeholder="base" v-model="lado1">
        <input type="number" id="lado2" placeholder="altura" v-model="lado2">
        <input type="button" value="Calcular" @click="calcular" class="botao">
    </div>

    <div>
        <h1>a área é {{ area }}</h1>
        <h1>o volume é {{ volume }}</h1>
        <h1>o perimetro é {{ perimetro }}</h1>

    </div>
</template>

<script lang="ts">

const lado1 = ref(0)
const lado2 = ref(0)

const area = ref(0)
const volume = ref(0)
const perimetro = ref(0)

const calcular = () => {
    try {
        const data = useFetch('https://localhost:8000/api/prisma', {
            method: 'POST',
            body: JSON.stringify({ lado1, lado2}),
        })

        area = data.area
        volume = data.volume
        perimetro = data.perimetro
    } catch (e) {
        console.log(e)
    }
}


    

</script>


<style scoped>

.prisma {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-left: 100px;
}
.botao {

    margin-left: 100px;
    background-color: aqua;
    border-radius: 10px;

}

</style>