<script setup>
    import { ref } from 'vue'
    const props = defineProps(
        ["knjiga"]
    )
</script>

<template>
    <div class="flex flex-col gap-2 items-center">
        <img :src="knjiga.slika" :alt="knjiga.naslov"
    class="w-32 h-48 rounded object-cover">
    </div>
</template>