<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <KeepAlive>
      <div class="column is-three-quarter">
        <FormularioTarefa @salvarTarefa="adicionarTarefa" />
        <!-- Lista de Tarefas -->
        <div class="lista">
          <ListaTarefas v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
          
          <BoxTarefa v-if="listaEstaVazia">
            Nenhuma tarefa cadastrada hoje
          </BoxTarefa>
        </div>

      </div>
    </KeepAlive>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTarefa from './components/FormularioTarefa.vue';
import ListaTarefas from './components/ListaTarefas.vue';

import type ITarefa from './interfaces/ITarefa';
import BoxTarefa from './components/BoxTarefa.vue';


export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioTarefa,
    ListaTarefas,
    BoxTarefa
  },
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    adicionarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    }
  }
});
</script>

<style scoped>
.lista {
  padding: 1.25rem;
}
</style>
