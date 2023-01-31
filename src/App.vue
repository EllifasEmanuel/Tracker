<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter">
      <TrackerFormulário @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TrackerTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>

      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import TrackerFormulário from './components/Formulario.vue'
import TrackerTarefa from './components/Tarefa.vue'
import InterfaceTarefa from './interfaces/InterfaceTarefa'
export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    TrackerFormulário,
    TrackerTarefa
  },
  data () {
    return {
      tarefas: [] as InterfaceTarefa[]
    }
  }, 
  methods: {
    salvarTarefa (tarefa: InterfaceTarefa) {
      this.tarefas.push(tarefa)
    }
  }
});
</script>

<style>
  .lista {
    padding: 1.25rem;
  }
</style>
