<!-- Tarea-App.vue -->
<template>
    <div>
        <h1>Algo</h1>
        <TareaForm />
    </div>
</template>
  
<script>
import { provide, ref } from 'vue'
import TareaForm from './TareaForm.vue'

export default {
    name: "Tarea-App",

    components: { TareaForm },

    setup() {
        const arregloTareas = ref([])
        provide('arregloTareas', arregloTareas)
    }


}
</script>
  