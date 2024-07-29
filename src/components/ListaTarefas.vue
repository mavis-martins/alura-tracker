<template>
    <BoxTarefa>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroTarefa :tempo-em-segundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxTarefa>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroTarefa from './CronometroTarefa.vue';

import type ITarefa from '../interfaces/ITarefa';
import BoxTarefa from './BoxTarefa.vue';

export default defineComponent({
    name: 'ListaTarefas',
    components: {
        CronometroTarefa,
        BoxTarefa
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
});
</script>