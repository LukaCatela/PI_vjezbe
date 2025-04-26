<script setup>
    import { ref } from 'vue';
    import Slika from './Slika.vue';
    const galerija = ref([    
        {
            slikar: "Pablo Picasso",
            godina: 1903,
            naslov: "The Old Guitarist",
            slika: "/src/assets/slike/The Old Guitarist.png"
        },
        {
            slikar: "Vincent van Gogh",
            godina: 1886,
            naslov: "Le Moulin de Blute-Fin",
            slika: "/src/assets/slike/Le Moulin de Blute-Fin.png"
        },
        {
            slikar: "Hokusai",
            godina: 1890,
            naslov: "Courtesan Asleep",
            slika: "/src/assets/slike/Courtesan Asleep.png"
        },
    ]);

    const povecana_slika = ref("");

</script>

<template>
    <div>
        ZADATAK 3
    </div>
    <div style="display: flex; gap: 10px;">
        <Slika v-for="slika in galerija"
        :slikar="slika.slikar"
        :godina="slika.godina"
        :naslov="slika.naslov"
        :slika="slika.slika"
        @povecaj="povecana_slika=slika.slika"/>
    </div>
    <br>
    <img :src="povecana_slika">
</template>

