<template>
    <BoxMessage>
        <div class="columns">
            <div class="column is-7">
                <p>{{tarefa.descricao || 'Tarefa sem descrição'}}</p>
            </div>
        </div>
        <div class="column">
            <TrackerCronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
        </div>
    </BoxMessage>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import TrackerCronometro from './Cronometro.vue';
import InterfaceTarefa from '../interfaces/InterfaceTarefa';
import BoxMessage from './BoxMessage.vue';
export default defineComponent ({
    name: 'TrackerTarefa',
    components: {
        TrackerCronometro,
        BoxMessage
    },
    props: {
        tarefa: {
            type: Object as PropType<InterfaceTarefa>,
            required: true
        }
    }
})
</script>