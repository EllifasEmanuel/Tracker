<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                <p>{{tarefa.descricao}}</p>
            </div>
        </div>
        <div class="column">
            <TrackerCronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import TrackerCronometro from './Cronometro.vue'
import InterfaceTarefa from '../interfaces/InterfaceTarefa'

export default defineComponent ({
    name: 'TrackerTarefa',
    components: {
        TrackerCronometro
    },
    props: {
        tarefa: {
            type: Object as PropType<InterfaceTarefa>,
            required: true
        }
    }
})
</script>

<style scoped>
    .box{
        background: #FAF0CA;
    }
</style>
