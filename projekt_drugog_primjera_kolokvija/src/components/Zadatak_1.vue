<script setup>
    import { ref,computed } from 'vue'
    const broj1 = ref(0)
    const broj2 = ref(0)
    const operacija = ref("")
    const provjeraOperacije = computed(() =>{
        if (
        operacija.value === "zbrajanje" || 
        operacija.value === "oduzimanje" || 
        operacija.value === "mnozenje" || 
        operacija.value === "dijeljenje")
        return true;
    })
</script>

<template>
    <div>
        ZADATAK 1
    </div>
    <input type="text" v-model="broj1">
    <input type="text" v-model="broj2">
    <input type="text" v-model="operacija">
    <hr>
    <div v-if="!provjeraOperacije">Nepoznata operacija!</div>
    <div v-if="operacija == 'zbrajanje'">{{ broj1 + broj2 }}</div>
    <div v-if="operacija == 'oduzimanje'">{{ broj1 - broj2 }}</div>
    <div v-if="operacija == 'mnozenje'">{{ broj1 * broj2 }}</div>
    <div v-if="operacija == 'dijeljenje'">
       <div v-if="broj1 == '0' || broj2 == '0'">
            Broj nije moguce dijelit s 0!
       </div>
       <div v-else>{{ broj1 / broj2 }}</div>
    </div>
</template>
