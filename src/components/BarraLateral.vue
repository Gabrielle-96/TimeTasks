<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="Alura Traker">
        </h1>
        <button class="button" @click="alterarTema">
            {{ textoBotao }}
        </button>
        <nav class="panel mt-5">
            <ul class="mt-5">
                <li class="link-text">
                    <router-link to="/">
                        <i class="fas fa-tasks"></i>
                        Tarefas
                    </router-link>
                </li>
                <li class="link-text mt-5">
                    <router-link to="/projetos">
                        <i class="fas fa-project-diagram"></i>
                        Projetos
                    </router-link>
                </li>
            </ul>
        </nav>
    </header>
</template>
  
<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
    name: 'BarraLateral',
    emits: ['alterarTema'],
    data() {
        return {
            modoEscuro: false
        }
    },
    computed: {
        textoBotao() {
            if (this.modoEscuro) {
                return 'Desativar modo escuro'
            }
            return 'Ativar modo escuro'
        }
    },
    methods: {
        alterarTema() {
            this.modoEscuro = !this.modoEscuro
            this.$emit('alterarTema', this.modoEscuro)
        }
    }
})
</script>
  
<style scoped>
header {
    padding: 1rem;
    background: #450d66f8;
    width: 100%;
    height: 100vh;
    text-align: center;
}

.link-text a {
    color: #fff;
    text-decoration: none;
}

.button {
    margin-top: 5rem;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>