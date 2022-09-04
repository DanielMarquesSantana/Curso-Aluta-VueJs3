<template>
    <section>
        <strong class="display">
            {{ tempoDecorido }}
        </strong>
    </section>
</template>

<script lang="ts">
    import { defineComponent } from 'vue'

    export default defineComponent({
        name: 'Cronometro',
        props: {
            tempoEmSegundos: {
                type: Number,
                default: 0
            }
        },
        computed: {
        tempoDecorido () : string {
            return new Date(this.tempoEmSegundos * 1000).toISOString().substring(11,19)
        }
    },
    })
</script>

<style>
    .display {
        color: var(--texto-primario);
        background: var(--bg-primario);
    }
</style>