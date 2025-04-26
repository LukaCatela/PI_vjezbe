<script setup>
    import { computed, ref, useTemplateRef } from 'vue'

    const props = defineProps(['opis', 'završeno', 'prioritet'])
    defineEmits(["azurirajOpis","azurirajZavrseno"])
    const uredivanje = ref(false)
    const noviOpis = ref('')
    const unos = useTemplateRef('unosRef')

    const dopustenoUredivanje = computed(() => {
        return uredivanje.value && !props.završeno
    })
    function ukljucenoUredivanje(){
        if (props.završeno) return;
        noviOpis.value = props.opis;
        uredivanje.value = true;
        unos.value.focus();
    }
    function iskljucenoUredivanje(){
        
    }
</script>
<template>
    <div style="display: flex;">
        <div @click="$emit('azurirajZavrseno')">
            <div class="kvadratic" v-if="!završeno">

            </div>
            <div class="kvadratic_ispunjen" v-else>

            </div>
            <div
            :class="{precrtano: završeno}">
                {{ opis }}
            </div>
            <input type="text" ref="unosRef" v-model="noviOpis"
            :style="!dopustenoUredivanje ? 'max-widith: 0px;':'max-widith:auto;'">
        </div>
    </div>
</template>

<style scoped>
.kvadratic {
    height: 16px;
    width: 16px;
    border: solid 1px black;
}
.kvadratic_ispunjen {
    height: 16px;
    width: 16px;
    background: green;
}
.precrtano{
    text-decoration: line-through;
}
.input{
    border: 1px solid black;
}
</style>