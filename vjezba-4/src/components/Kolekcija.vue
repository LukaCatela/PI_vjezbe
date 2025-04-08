<script setup>
    import Knjiga from './Knjiga.vue';
    defineProps(["knjige"])
</script>

<template>

<div class="flex gap-2">
      <Knjiga v-for="knjiga in knjige" :naslov = "Knjiga.naslov" :slika ="Knjiga.slika"> 
        
      </Knjiga>

    </div>
</template>