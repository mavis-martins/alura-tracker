<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BarraLateral',
    emits: ['temaAlterado'],
    data() {
        return {
            temaEscuroAtivo: false
        }
    },
    computed: {
        textoBotao() {
            return this.temaEscuroAtivo ? 'Ativar Modo Claro' : 'Ativar Modo Escuro';
        } 
    },
    methods: {
        alterarTema(): void {
            this.temaEscuroAtivo = !this.temaEscuroAtivo;
           this.$emit('temaAlterado', this.temaEscuroAtivo);
        }
    }
});
</script>

<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="Logo Alura Tracker">
        </h1>

        <button class="button" @click="alterarTema">
            {{ textoBotao }}
        </button>
    </header>
</template>

<style scoped>
    header {
        padding: 1rem;
        background: #0d3b66;
        width: 100%;
        height: 100vh;
        text-align: center;
    }
    @media only screen and (max-width: 768px) {
        header {
            padding: 2.5rem;
            height: auto;
        }
    }
</style>