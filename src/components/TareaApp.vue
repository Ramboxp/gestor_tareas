<!-- Tarea-App.vue -->
<template>
    <h1 class="text-center">Tareas</h1>
    <TareaForm />
    <TareaList />
</template>
  
<script>
import { provide, ref, watchEffect } from 'vue'
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
        //LocalStoge
        if (localStorage.getItem('arregloTareas')) {
            arregloTareas.value = JSON.parse(localStorage.getItem('arregloTareas'))
        }

        watchEffect(() => {
            localStorage.setItem('arregloTareas', JSON.stringify(arregloTareas.value))
        })
    }
}
</script>
