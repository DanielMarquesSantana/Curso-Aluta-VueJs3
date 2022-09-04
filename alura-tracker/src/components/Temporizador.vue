<template>
    <div class="column">
        <div class="is-flex is-aling-items-center is-justify-content-space-between">
            <Cronometro :tempoEmSegundos="tempoEmSegundos" />
            <Botao @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
            <Botao @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
        </div>
    </div>
</template>

<script lang="js">
import { defineComponent } from 'vue'
import Cronometro from './Cronometro.vue'
import Botao from './Botao.vue'

export default defineComponent({
    name: 'Temporizador',
    emits: ['aoTemporizadorFinalizado'],
    components: {
        Cronometro,
        Botao
    },
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods: {
        iniciar() {
            // comecar a contagem
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1
            }, 1000)
            console.log('Iniciando');
            this.cronometroRodando=true;
        },
        finalizar() {
            console.log('Finalizando');
            this.cronometroRodando=false;
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
})
</script>