<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuro }">
    <div class="column is-one-quarter">
      <BarraLateral @alterarTema="temaAlterado" />
    </div>
    <div class="column is-three-quarters conteudo">
      <router-view></router-view>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
  },
  data() {
    return {
      modoEscuro: false
    }
  },

  methods: {
    temaAlterado(modoEscuro: boolean) {
      this.modoEscuro = modoEscuro
    }
  },
});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
  --texto-secundario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
  --texto-secundario: #FFF;
}

.texto-color {
  color: var(--texto-secundario)
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>