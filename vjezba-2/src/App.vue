<script setup>
  import { ref,computed } from 'vue'
      const slike = ref({
        "Jabuka": "https://www.svgrepo.com/show/530203/apple.svg",
        "Mrkva": "https://www.svgrepo.com/show/530216/carrot.svg",
        "Sir": "https://www.svgrepo.com/show/530219/cake.svg",
        "Kruh": "https://www.svgrepo.com/show/530223/bread.svg",
        });
      const proizvodi = ref([
          { naziv: "Jabuka", cijena: 0.25 },
          { naziv: "Mrkva", cijena: 0.12 },
          { naziv: "Kruh", cijena: 2.00 },
          { naziv: "Sir", cijena: 4.48 }
          ]);
      const korisnik = ref({
          jeAdmin: false,
          osobni_podaci: {
          ime: "Marko",
          prezime: "Krivić",
          adresa: {
          grad: "Pula",
          ulica: "Veruda",
          broj: 32
          },
        broj_telefona: "+091-123-456"
        },
        kosarica :[
        { naziv: "Jabuka", količina: 4 },
        { naziv: "Mrkva", količina: 12 },
        { naziv: "Sir", količina: 1 },
        { naziv: "Kruh", količina: 3 },
        ]
      })

function dohvatiCijenu(naziv){
  const proizvod = proizvodi.value.find(p=> p.naziv == naziv)
  return proizvod ? proizvod.cijena : 0
}

function sveukupnaCijena() {
  let ukupno = 0;
  for (const item of korisnik.value.kosarica) {
    const proizvod = proizvodi.value.find(p => p.naziv === item.naziv);
    if (proizvod) {
      ukupno += proizvod.cijena * item.količina;
    }
  }
  return ukupno.toFixed(2);
}

function najskupljaStavka(){
  let najskuplja = null;
  let max = 0;
  for (const item of korisnik.value.kosarica) {
    const proizvod = proizvodi.value.find(p => p.naziv === item.naziv);
    if (proizvod) {
      const ukupnacijena = proizvod.cijena * item.količina;
      if(ukupnacijena > max){
        max = ukupnacijena;
        najskuplja = item.naziv;
      }
    }
  }
  return najskuplja;
}
const punoIme = computed(()=> `${korisnik.value.osobni_podaci.ime} ${korisnik.value.osobni_podaci.prezime}`) //Tu sam koristio drugu notaciju zapisa varijable
const adresa_korisnik = computed(()=> korisnik.value.osobni_podaci.adresa.ulica + korisnik.value.osobni_podaci.adresa.broj + "," + korisnik.value.osobni_podaci.adresa.grad)
const telefon_korisnik = computed(()=> korisnik.value.osobni_podaci.broj_telefona);

</script>

<template>
  <div class="flex flex-col justify-center items-center h-screen">
    <div class="bg-blue-50 w-1/4 h-auto rounded-sm p-2 text-left"
      :class="korisnik.jeAdmin ? 'text-blue-600' : 'text-black'">
      <span><b>Korisnički podaci</b></span>
      <hr>
      <span ><b>Ime: </b>{{ punoIme }}</span><br>
      <span><b>Adresa: </b>{{ adresa_korisnik }}</span> <br>
      <span><b>Telefon: </b>{{ telefon_korisnik }}</span>
    </div>
      <div class="bg-blue-50 w-1/4 h-auto rounded-sm p-2 text-left mt-4 flex flex-col items-center shadow">
      <span class="text-2xl"><b>Košarica</b></span><br>
        <div class="mb-2 p-2 rounded"
        :class="korisnik.kosarica[0].naziv === najskupljaStavka() ? 'bg-red-200' : 'bg-gray-100'">
          <img :src="slike[korisnik.kosarica[0].naziv]" class="w-8 inline-block">
        </div>
      </div>
  </div>
</template>