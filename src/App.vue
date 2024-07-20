<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="addTarefa" />
      <div class="lista">
        <TarefaComponent v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <CustomBox v-if="listaVazia">
          O cavalo está cansado?
        </CustomBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import BarraLateral from './components/BarraLateral.vue';
import { defineComponent } from 'vue';
import Formulario from './components/Formulario.vue';
import TarefaComponent from './components/TarefaComponent.vue';
import ITarefa from './interfaces/ITarefa'
import CustomBox from './components/CustomBox.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral, Formulario, TarefaComponent, CustomBox
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listaVazia() : boolean{
      return this.tarefas.length === 0;
    }
  },
  methods: {
    addTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },

    trocarTema(modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo;
    }
  }
});
</script>

<style>
.list {
  padding: 10px;
}

main{
  --bg-primario: white;
  --texto-primario: black;
}

main.modo-escuro{
  --bg-primario: black;
  --texto-primario: white;
}

.conteudo{
  background-color:var(--bg-primario);
}
</style>
