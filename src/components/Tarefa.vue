<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || "Tarefa sem descrição" }}
            </div>
            <div class="column">
                <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"></Cronometro>
            </div>
        </div>

    </Box>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Cronometro from "./Cronometro.vue";
import ITarefa from "@/interfaces/ITarefa";
import Box from "./Box.vue";

export default defineComponent({
    name: "Tarefa",
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    },
    data() {
        return {
            descricaoTarefa: ""
        };
    },
    components: {
        Cronometro,
        Box
    }
})
</script>

<style scoped>
</style>