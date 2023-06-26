<template>
  <main class="columns is-gapless is multiline" :class="{ 'escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>

    <div class="column is-tree-quarsalvarTarefater conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <Tarefa
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tarefa="tarefa"
        />
        <box v-if="listaEstaVazia"> Você não está muito produtivo hoje :( </box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import Box from "./components/Box.vue";
import Formulario from "./components/Formulario.vue";
import Tarefa from "./components/Tarefa.vue";
import ITarefa from "./interfaces/ITarefa";

export default defineComponent({
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box,
  },
  name: "app",
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    };
  },

  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length == 0;
    },
  },

  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
    trocarTema (modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
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
  --bg-secundario: #444E6F;
  --texto-primario: #4BC0A0;
}
main.escuro {
  --bg-primario: #18191B;
  --bg-secundario: #4BC0A0;
  --texto-primario: #444E6F;
}
.conteudo {
  background-color: var(--bg-primario);
}
.box {
  border-radius: 0px;
}
</style>
