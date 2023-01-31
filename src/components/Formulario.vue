<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para a criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>
            
            <div class="column">
                <TrackerTemporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue'
    import TrackerTemporizador from './Temporizador.vue'

    export default defineComponent ({
        name: 'TrackerFormulário',
        emits: ['aoSalvarTarefa'],
        components: {
            TrackerTemporizador
        },
        data () {
            return {
                descricao: ''
            }
        },
        methods: {
            finalizarTarefa (tempoDecorrido: number) : void {
                this.$emit('aoSalvarTarefa', {
                    duracaoEmSegundos: tempoDecorrido,
                    descricao: this.descricao
                })
                this.descricao = ''
            }
        }
    })
</script>