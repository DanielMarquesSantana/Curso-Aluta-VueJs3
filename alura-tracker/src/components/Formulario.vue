<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario para criacao de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual terefa deseja iniciar?" v-model="descricao">
            </div>
            <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
        </div>
    </div>
</template>


<script lang="ts">
import { defineComponent } from 'vue'
import Temporizador from './Temporizador.vue'

export default defineComponent({
    name: 'Formulario',
    emits: ['aoSalvarTarefa'],
    components: {
        Temporizador
    },
    data () {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa (tempoDecorido: number) :void {
            console.log('Tempo da tarefa:' + tempoDecorido)
            console.log('Descricao da tarefa:' + this.descricao)
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoDecorido,
                descricaoTarefa: this.descricao
            })
            this.descricao = ''
        }
    }
})
</script>

<style>
    .formulario {
        color: var(--texto-primario);
        background: var(--bg-primario);
    }
</style>