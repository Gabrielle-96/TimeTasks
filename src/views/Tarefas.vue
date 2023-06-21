<template>
    <div class="column is-three-quarter conteudo">
        <Formulario @aoSalvarTarefa="salvarTarefa" />
        <div class="lista">
            <Box v-if="listaVazia" class="texto-color">
                Você ainda não registrou sua produtividade hoje :(
            </Box>
            <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        </div>
    </div>
</template>
  
<script lang="ts">
import { defineComponent } from 'vue';
import Formulario from '../components/Formulario.vue'
import Tarefa from '../components/Tarefa.vue'
import Box from '../components/Box.vue'
import ITarefa from '../interfaces/ITarefa'
export default defineComponent({
    name: 'App',
    components: {
        Formulario,
        Tarefa,
        Box
    },
    data() {
        return {
            tarefas: [] as ITarefa[],
        }
    },
    methods: {
        salvarTarefa(tarefa: ITarefa) {
            this.tarefas.push(tarefa)
        }
    },
    computed: {
        listaVazia(): boolean {
            return this.tarefas.length === 0
        }
    }
});
</script>
