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

function ukupnaCijena(naziv) {
  const cijena = dohvatiCijenu(naziv);
  const stavka = korisnik.value.kosarica.find(k => k.naziv === naziv);
  return stavka ? (cijena * stavka.količina).toFixed(2) : "0.00";
}


function najskupljaStavka() {
  let najskuplja = null;
  let max = 0;
  for (const item of korisnik.value.kosarica) {
    const cijena = dohvatiCijenu(item.naziv);
    const ukupno = cijena * item.količina;
    if (ukupno > max) {
      max = ukupno;
      najskuplja = item.naziv;
    }
  }
  return najskuplja;
}

const sveukupnaCijena = computed(() =>
  korisnik.value.kosarica
    .reduce((ukupno, item) => ukupno + dohvatiCijenu(item.naziv) * item.količina, 0)
    .toFixed(2)
);


const punoIme = computed(()=> `${korisnik.value.osobni_podaci.ime} ${korisnik.value.osobni_podaci.prezime}`) //Tu sam koristio drugu notaciju zapisa varijable
const adresa_korisnik = computed(()=> korisnik.value.osobni_podaci.adresa.ulica + korisnik.value.osobni_podaci.adresa.broj + "," + korisnik.value.osobni_podaci.adresa.grad)
const telefon_korisnik = computed(()=> korisnik.value.osobni_podaci.broj_telefona);

</script>

<template>
  <div class="flex flex-col justify-center items-center h-screen">
    <div class="bg-blue-50 w-2/6 h-auto rounded-sm p-2 text-left"
      :class="korisnik.jeAdmin ? 'text-blue-600' : 'text-black'">
      <span><b>Korisnički podaci</b></span>
      <hr>
      <span ><b>Ime: </b>{{ punoIme }}</span><br>
      <span><b>Adresa: </b>{{ adresa_korisnik }}</span> <br>
      <span><b>Telefon: </b>{{ telefon_korisnik }}</span>
    </div>
      <div class="bg-blue-50 w-2/6 h-auto rounded-sm p-2 text-left mt-4 flex flex-col items-center shadow">
      <span class="text-2xl"><b>Košarica</b></span><br>

        <!--JABUKA-->
        <div class="my-3 border p-2 rounded w-6/7"
            :class="korisnik.kosarica[0].naziv === najskupljaStavka() ? 'bg-red-200' : 'bg-gray-50'">
          <div class="flex items-center gap-4">
          <img :src="slike[korisnik.kosarica[0].naziv]" class="w-12 h-12 object-contain">
          <div class="flex flex-col">
            <b class="text-lg">{{ korisnik.kosarica[0].naziv }}</b>
            <span>Cijena: €{{ dohvatiCijenu("Jabuka") }} | Količina: {{ korisnik.kosarica[0].količina }}</span>
            <span>Ukupno: €{{ ukupnaCijena("Jabuka") }}</span>
          </div>
          </div>
        </div>
        <!-- MRKVA -->
        <div class="my-3 border p-2 rounded w-6/7"
            :class="korisnik.kosarica[1].naziv === najskupljaStavka() ? 'bg-red-200' : 'bg-gray-50'">
          <div class="flex items-center gap-4">
            <img :src="slike[korisnik.kosarica[1].naziv]" class="w-12 h-12 object-contain">
            <div class="flex flex-col">
              <b class="text-lg">{{ korisnik.kosarica[1].naziv }}</b>
              <span>Cijena: €{{ dohvatiCijenu('Mrkva') }} | Količina: {{ korisnik.kosarica[1].količina }}</span>
              <span>Ukupno: €{{ ukupnaCijena('Mrkva') }}</span>
            </div>
          </div>
        </div>

        <!-- KRUH -->
        <div class="my-3 border p-2 rounded w-6/7"
            :class="korisnik.kosarica[3].naziv === najskupljaStavka() ? 'bg-red-200' : 'bg-gray-50'">
          <div class="flex items-center gap-4">
            <img :src="slike[korisnik.kosarica[3].naziv]" class="w-12 h-12 object-contain">
            <div class="flex flex-col">
              <b class="text-lg">{{ korisnik.kosarica[3].naziv }}</b>
              <span>Cijena: €{{ dohvatiCijenu('Kruh') }} | Količina: {{ korisnik.kosarica[3].količina }}</span>
              <span>Ukupno: €{{ ukupnaCijena('Kruh') }}</span>
            </div>
          </div>
        </div>

        <!-- SIR -->
        <div class="my-3 border p-2 rounded w-6/7"
            :class="korisnik.kosarica[2].naziv === najskupljaStavka() ? 'bg-red-200' : 'bg-gray-50'">
          <div class="flex items-center gap-4">
            <img :src="slike[korisnik.kosarica[2].naziv]" class="w-12 h-12 object-contain">
            <div class="flex flex-col">
              <b class="text-lg">{{ korisnik.kosarica[2].naziv }}</b>
              <span>Cijena: €{{ dohvatiCijenu('Sir') }} | Količina: {{ korisnik.kosarica[2].količina }}</span>
              <span>Ukupno: €{{ ukupnaCijena('Sir') }}</span>
            </div>
          </div>
        </div>

        <br>
        <span><b>Ukupna cijena:</b>€ {{ sveukupnaCijena }}</span>
      </div>
  </div>
</template>