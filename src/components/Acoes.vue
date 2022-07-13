<template>
    <div class="box acoes">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?"
                    v-model="descricaoTarefa">
            </div>
            <div class="column">
                <Temporizador @aoTemporizadorFinalizado="finalizarTarefa" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import Temporizador from "./Temporizador.vue"

export default defineComponent({
    name: "Acoes",
    components: {
        Temporizador
    },
    emits: ["aoRegistrarTarefa"],
    data() {
        return {
            descricaoTarefa: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number): void {
            this.$emit("aoRegistrarTarefa", {
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricaoTarefa 
            })
            this.descricaoTarefa = ''
        }
    }
})
</script>

<style>
.acoes {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>