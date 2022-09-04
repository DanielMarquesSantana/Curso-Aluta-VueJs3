<template>
    <div class="box has-text-weigth-bold" :style="estilos">
        <slot></slot>
    </div>
</template>
<script lang="ts">

    import { defineComponent } from 'vue';
    export default defineComponent({
        name: 'Box',
        data () {
            return {
                estilos: {
                    background: '#FAF0CA'
                }
            }
        }
    })

</script>

<style scoped> /* Quando marca como scoped quer dizer que somente nesse componente sera aplicado o estilo*/
    /* .box {
        background: #FAF0CA
    } */
</style>