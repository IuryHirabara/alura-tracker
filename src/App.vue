<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"></BarraLateral>
    </div>
    <div class="column is-three-quarter conteudo">
      <Acoes @aoRegistrarTarefa="registraTarefa"></Acoes>
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"></Tarefa>
        <Box v-if="verficaLista">
          Vazio
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import Vue from 'vue'
import BarraLateral from './components/BarraLateral.vue'
import Acoes from './components/Acoes.vue'
import Tarefa from './components/Tarefa.vue';
import Box from './components/Box.vue';
import ITarefa from './interfaces/ITarefa.vue';

export default Vue.extend({
  name: "App",
  components: {
    BarraLateral,
    Acoes,
    Tarefa,
    Box
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    verficaLista(): boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    registraTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    trocarTema(modoEscuroAtivado: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivado
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem
}

main {
  --bg-primario: #FFF;
  --texto-primario: #000
}

main.modo-escuro {
  --bg-primario: #2B2D42;
  --texto-primario: #DDD
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
