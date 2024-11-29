<template>
    <div>

        <URadio v-for="option of options" :key="option.value" v-model="selected" v-bind="option" />

        
    </div>
    <div>
        <Cilindro v-if="selected == 'cilindro'"></Cilindro>
        <Prisma v-if="selected == 'prisma'"></Prisma>
        <Cubo v-if="selected == 'cubo'"></Cubo>
        <Esfera v-if="selected == 'esfera'"></Esfera>
    </div>
</template>

<script setup lang="ts">
import Cubo from '~/components/Cubo.vue';

    const options = [
        { label: 'Cilindro', value: 'cilindro' },
        { label: 'Cubo', value: 'cubo' },
        { label: 'Esfera', value: 'esfera' },
        {label: 'prisma', value: 'prisma'},
    ]
    const selected = ref('')

    watch(selected, () => {
        console.log(selected.value)
    })


</script>


<style lang="scss" scoped>

</style>