<script setup>
import { ref, computed } from 'vue';
const proizvodi =ref([]);
const naziv_proizvod = ref("");
const cijena_proizvod = ref(1);
 // funkcije
function dodajArtikl(){
    proizvodi.value.push({
        naziv: naziv_proizvod.value,
        cijena: parseFloat(cijena_proizvod.value),
        kolicina: 1,
    })
    naziv_proizvod.value = ''
    cijena_proizvod.value = 1
}
function ukupno_proizvod(proizvod) {
  return (proizvod.cijena * proizvod.kolicina).toFixed(2)
}
const ukupno = computed(() => {
  return proizvodi.value.reduce((acc, proizvod) => {
    return acc + proizvod.cijena * proizvod.kolicina
  }, 0).toFixed(2)
})

function povecaj_kolicina_proizvoda (index){
    proizvodi.value[index].kolicina++
}
function smanji_kolicina_proizvoda(index){
    proizvodi.value[index].kolicina--
}

function ukloni_proizvod(index){
    proizvodi.value.splice(index,1)
}
</script> 

<template>
    <div class="h-full flex items-center justify-center bg-white p-4">
         <div class="bg-gray-100 p-6 rounded-2xl shadow-md w-60/100">
                 <h1 class="text-3xl font-bold mb-4">Košarica</h1>
                 <br>
                 <hr>
                 <div class="inline-block p-2">
                     <span>Naziv proizvoda: </span>
                     <input type="text" v-model="naziv_proizvod" placeholder="Upiši naziv artikla..." class="bg-white rounded-md  border-1 m-2">
                     <span>Cijena proizvoda:</span>
                     <input type="text" v-model="cijena_proizvod" class="bg-white rounded-md  border-1 m-2">
                     <button class="border-1 rounded-3xl p-2 bg-green-600 hover:bg-green-400" @click="dodajArtikl"><b>Dodaj artikl</b></button>
                 </div>
                 <hr>
                 <div class="flex justify-between text-gray-600 font-semibold w-full max-w-4xl mx-auto">
                 <span>Artikl</span>
                 <span>Količina</span>
                 <span>Cijena</span>
                 <span>Ukupno</span>
                 <span></span>
                 </div>
                 <div class="flex justify-between items-center text-gray-600" v-for="(proizvod, index) in proizvodi" :key='index'>
                     <span>{{ proizvod.naziv }}</span>
                     <div class="flex items-center space-x-5">
                         <button @click="smanji_kolicina_proizvoda(index)" class="text-red-500 mx-1">-</button>
                         <span class="bg-white rounded-md border-0 m-2">{{ proizvod.kolicina }}</span>
                         <button @click="povecaj_kolicina_proizvoda(index)" class="text-green-500 mx-1">+</button>
                     </div>
                     <span>{{ proizvod.cijena.toFixed(2) }}</span>
                     <span>{{ ukupno_proizvod(proizvod) }}</span>
                     <button @click="ukloni_proizvod(index)" class="text-red-600">Ukloni</button>
                 </div>
 
                 <hr>
                 <div class="p-2">
                     <b>UKUPNO: {{ ukupno }}</b>
                 </div>
 
         </div>
    </div>
 </template>