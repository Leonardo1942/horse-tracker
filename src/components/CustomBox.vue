<template>
        <div class="box has-text-weight-bold">
            <slot></slot>
        </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'CustomBox',
})
</script>

<style>
.box {
    background-color: var(--bg-primario);
    border: 1px solid var(--texto-primario) ;
    color: var(--texto-primario);
    margin: 3px;
}
</style>