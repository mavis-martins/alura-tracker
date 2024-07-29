<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroTarefa :tempo-em-segundos="tempoEmSegundos" />
        <BotaoTemporizador texto="play" icone="fas fa-play" :desabilitado="cronometroRodando" @clicado="iniciarTarefa" />
        <BotaoTemporizador texto="stop" icone="fas fa-stop" :desabilitado="!cronometroRodando" @clicado="finalizarTarefa" />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'FormularioTarefa',
    emits: ['aoTemporizadorFinalizado'],
    components: {
        CronometroTarefa,
        BotaoTemporizador
    },
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods: {
        iniciarTarefa() {
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos++;
            }, 1000)

            this.cronometroRodando = true;
        },
        finalizarTarefa() {
            clearInterval(this.cronometro);

            this.cronometroRodando = false;

            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        }
    }
});

import CronometroTarefa from './CronometroTarefa.vue';
import BotaoTemporizador from './BotaoTemporizador.vue';


</script>

<style scoped></style>