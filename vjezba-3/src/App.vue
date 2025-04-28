<script setup>
import { ref, computed } from 'vue';

const naziv_proizvod = ref("");
const cijena_proizvod = ref(1);
 // funkcije
 const povecajCijenu = computed(() => {
    
 })

</script> 

<template>
   <div class="h-full flex items-center justify-center bg-white p-4">
        <div class="bg-gray-100 p-6 rounded-2xl shadow-md w-60/100">
                <h1><b>Košarica</b></h1>
                <br>
                <hr>
                <div class="inline-block p-2">
                    <span>Naziv proizvoda: </span>
                    <input type="text" placeholder="Upiši naziv artikla..." class="bg-white rounded-md  border-1 m-2">
                    <span>Cijena proizvoda:</span>
                    <input type="text" class="bg-white rounded-md  border-1 m-2">
                    <button class="border-1 rounded-3xl p-2 bg-green-600 hover:bg-green-400"><b>Dodaj artikl</b></button>
                </div>
                <hr>
                <div class="flex justify-between text-gray-600 font-semibold w-full max-w-4xl mx-auto">
                <span>Artikl</span>
                <span>Količina</span>
                <span>Cijena</span>
                <span>Ukupno</span>

                </div>

                <hr>
                <div class="p-2">
                    <b>UKUPNO: {{ ukupno }}</b>
                </div>

        </div>
   </div>
</template>