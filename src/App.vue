<template>
  <main class="columns is-gapless is-multiline modo-escuro">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter conteudo">
      <TrackerFormulário @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TrackerTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxMessage v-if="listaEstaVazia">
          Você não está sendo muito produtivo hoje. :(
        </BoxMessage>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import TrackerFormulário from './components/Formulario.vue';
import TrackerTarefa from './components/Tarefa.vue';
import InterfaceTarefa from './interfaces/InterfaceTarefa';
import BoxMessage from './components/BoxMessage.vue';
export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    TrackerFormulário,
    TrackerTarefa,
    BoxMessage
  },
  data () {
    return {
      tarefas: [] as InterfaceTarefa[]
    }
  },
  computed: {
    listaEstaVazia () : boolean {
      return this.tarefas.length === 0
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
