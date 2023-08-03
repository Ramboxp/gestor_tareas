<!-- Tarea-App.vue -->
<template>
 
        <h1>Algo</h1>

        <TareaForm />
        <TareaList />

</template>
  
<script>
import { provide, ref } from 'vue'
import TareaForm from './TareaForm.vue'
import TareaList from './TareaList.vue'

export default {
    name: "Tarea-App",

    components: {
        TareaForm,
        TareaList
    },

    setup() {
        const arregloTareas = ref([])
        provide('arregloTareas', arregloTareas)
    }
}
</script>
  