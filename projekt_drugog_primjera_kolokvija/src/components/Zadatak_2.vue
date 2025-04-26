<script setup>
    import { ref,computed } from 'vue';
    import { TransitionGroup } from 'vue';

    const sportasi = ref([
        {
            ime: 'Ivan', 
            disciplina: 'plivanje', 
            godine: 25, 
            natjecanja: ['Olimpijske igre', 'Svjetsko prvenstvo']
        },
        {
            ime: 'Ana', 
            disciplina: 'atletika', 
            godine: 30, 
            natjecanja: ['Svjetsko prvenstvo', 'Europsko prvenstvo', 'Olimpijske igre']
        },
        {
            ime: 'Marko', 
            disciplina: 'odbojka', 
            godine: 22, 
            natjecanja: ['Europsko prvenstvo']
        }
    ])

    const novo_natjecanje = ref('');

    function dodaj_natjecanje(sportas){
        const index = sportasi.value.indexOf(sportas);
        if (index !== -1 && novo_natjecanje.value.trim() !== '') {
            sportasi.value[index].natjecanja.push(novo_natjecanje.value.trim());
            novo_natjecanje.value = '';
        }
    }

function ukloni_natjecanje(sportas, natjecanje_Index){
    const index = sportasi.value.indexOf(sportas);
    if (index !== -1) {
        sportasi.value[index].natjecanja.splice(natjecanje_Index, 1);
    }
}


    const sortirani_sportasi = computed(() =>{
        return [...sportasi.value].sort((a,b) => b.natjecanja.length - a.natjecanja.length)
    });
</script>

<template>
    <div>
        ZADATAK 2
    </div>
    <br>
    <input type="text" v-model="novo_natjecanje" placeholder="dodaj natjecanje">
    <hr>
    <div v-for="(sportas, index_sportas) in sortirani_sportasi" :key="index_sportas">
        <span>
            <span v-if="index_sportas === 0">🥇</span>
            <span v-else-if="index_sportas === 1">🥈</span>
            <span v-else-if="index_sportas === 2">🥉</span>
            <strong>{{ sportas.ime }}</strong> ({{ sportas.godine }} god) - {{ sportas.disciplina }}
        </span>
        <br>
        <b>Natjecanja:</b>        
        <button @click="dodaj_natjecanje(sportas)">+</button>        <TransitionGroup name="list" tag="ul">
            <li v-for="(natjecanje,i_natjecanje) in sportas.natjecanja" :key="natjecanje">
                <button @click="ukloni_natjecanje(sportas, i_natjecanje)">-</button>
                {{ natjecanje }}
            </li>
            <hr>
    </TransitionGroup>
    </div>
</template>

<style scoped>
.list-enter-active,
.list-leave-active {
transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
opacity: 0;
transform: translateX(30px);
}
ul {
  list-style-type: none;
  padding-left: 0;
}
</style>