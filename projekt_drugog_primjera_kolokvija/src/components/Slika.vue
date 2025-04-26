<script setup>
import { ref } from 'vue';

    const props = defineProps(['slikar','godina','naslov','slika'])
    function starost(){
        return 2025 - props.godina;
    }
    const emit = defineEmits(['povecaj'])
</script>
<template>

    <div>
        <img :src="slika" @click="$emit('povecaj')" height="100">
        <br>
        <b>Naslov</b><span :class="{'underline' : starost()>136}">{{ naslov }}</span><br>
        <b>Slikar</b>{{ slikar }} <br>
        <b>Godina</b>{{ godina }} <br>
    </div>
</template>
<style scoped>
.underline {
    text-decoration: underline;
}
</style>