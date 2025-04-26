<script setup>
    import { ref } from 'vue'
    import ToDoStavka from '@/components/ToDoStavka.vue';
    const stavke = ref([
        {
            opis: 'Implementirati uklanjanje',
            završeno: false,
            prioritet: 1,
        },
        {
            opis: 'Dodati text edit',
            završeno: true,
            prioritet: 2,
        },
        {
            opis: 'Implementirati pomicanje',
            završeno: false,
            prioritet: 4,
        },
        {
            opis: 'Dodati date',
            završeno: false,
            prioritet: 5,
        },
        {
            opis: 'Implementirati promjenu boje',
            završeno: false,
            prioritet: 6,
        }
        ])

</script>
<template>
    <hr>
    <div>
        <ToDoStavka
        v-for="stavka in stavke"
        :opis="stavka.opis"
        :završeno="stavka.završeno"
        :prioritet="stavka.prioritet"
        @azurirajZavrseno="stavka.završeno = !stavka.završeno"
        />
    </div>
    <hr>
</template>