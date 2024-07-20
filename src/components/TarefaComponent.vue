<template>
    <CustomBox>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>

            <div class="column">
                <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </CustomBox>
</template>

<script lang="ts">

import Cronometro from './Cronometro.vue';
import CustomBox from './CustomBox.vue';
import ITarefa from '../interfaces/ITarefa';
import { defineComponent, PropType } from 'vue';

export default defineComponent({
    name: 'TarefaComponent',
    components: {
        Cronometro,
        CustomBox
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true,
        },

    }
})

</script>
