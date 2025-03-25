<script setup>
import { ref } from 'vue'
const lozinka = ref("");

function provjeriVelikoSlovo(value) {
  const provjera = /[A-Z]/.test(value);
  return !provjera
}
function provjeriBroj(value) {
  const provjera = /[\d]/.test(value);
  return !provjera
}
function provjeriznak(value) {
  const provjera = /[!"=#$%&\*?=]/.test(value);
  return !provjera
}
function SveUredu(value){
  borjOK.value = 0;
  const prvaP = !provjeriVelikoSlovo(value);
  const drugaP = !provjeriBroj(value);
  const trecaP = !provjeriznak(value);
  const cetvrtaP = length >= 8;

  if(prvaP) borjOK.value++;
  if(drugaP) borjOK.value++;
  if(trecaP) borjOK.value++;
  if(cetvrtaP) borjOK.value++;

  return prvaP && drugaP && trecaP && cetvrtaP;
}
</script>

<template>
  <div class="h-screen flex flex-col justify-center items-center">
    <input type="text" placeholder="Upiši lozinku" class="border rounded px-1 w-68" v-model="lozinka">
  <div v-if="lozinka.length < 8" class="text-red-600">Lozinka mora imati 8 znakova</div>
  <div v-if="provjeriznak(lozinka)" class="text-red-600">Lozinka nema znak</div>
  <div v-if="provjeriVelikoSlovo(lozinka)" class="text-red-600">Lozinka nema veliko slovo</div>
  <b v-else-if="SveUredu(lozinka)">Lozinka je u redu</b>
  </div>
</template>

