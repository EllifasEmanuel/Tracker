<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <TrackerCronometro :tempoEmSegundos="tempoEmSegundos"/>
        <button class="button" @click="iniciar" :disabled="cronometroRodando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>PLAY</span>
        </button>
        <button class="button" @click="finalizar" :disabled="!cronometroRodando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>STOP</span>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TrackerCronometro from './Cronometro.vue'

export default defineComponent ({
    name: 'TrackerTemporizador',
    emits: ['aoTemporizadorFinalizado'],
    components: {
        TrackerCronometro
    },
    data () {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods: {
        iniciar () {
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1
            }, 1000)
        },
        finalizar () {
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
})
</script>