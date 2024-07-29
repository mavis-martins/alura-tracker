<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input 
                    type="text" 
                    v-model="descricaoTarefa"
                    class="input" 
                    placeholder="Qual tarefa você deseja iniciar?"
                >
            </div>
            <div class="column">
                <TemporizadorTarefa @ao-temporizador-finalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorTarefa from './TemporizadorTarefa.vue';

export default defineComponent({
    name: 'FormularioTarefa',
    emits: ['salvarTarefa'],
    components: {
        TemporizadorTarefa
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number): void {
            this.$emit('salvarTarefa', {
                descricao: this.descricaoTarefa,
                duracaoEmSegundos: tempoDecorrido
            });
            this.descricaoTarefa = '';
        }
    },
    data() {
        return {
            descricaoTarefa: ''
        }
    }
});
</script>

<style scoped></style>