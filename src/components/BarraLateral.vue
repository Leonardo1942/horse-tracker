<template>
    <header>
        <button class="button" style="margin: 5px;" @click="alterarTema">
           {{ textoBotao }}
        </button>
        <h1>
            <img src="../assets/logo.png" alt="imagem do cavalo do go horse process" style="border-radius: 20%; margin-top: 25px;">
        </h1>
    </header>
</template>

<script lang="ts">
import {defineComponent } from 'vue';

export default defineComponent({
    name: 'BarraLateral',
    emits:['aoTemaAlterado'],
    data() {
        return {
            modoEscuroAtivo: false
        }
    },
    computed:{
        textoBotao(){
            if(this.modoEscuroAtivo){
                return 'Desativar Modo Escuro'
            }

            return 'Ativar Modo Escuro'
        }
    },
    methods:{
        alterarTema(){
            this.modoEscuroAtivo = !this.modoEscuroAtivo
            this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
        }
    }
})
</script>

<style>
header {
    background: var(--bg-primario);
    width: 100%;
    height: 100vh;
}

img{
    margin-left: 25%;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}

@media only screen and (max-width: 1246px) {
  img{
    width: 10rem;
  }
}
</style>