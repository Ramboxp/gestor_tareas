<!-- TareaForm.vue -->
<template>
    <form @submit.prevent="agregarTarea">
        <input type="text" class="form-control my-3" placeholder="Ingrese tarea" v-model.trim="texto" required>
    </form>
</template>
  
<script>
/* eslint-disable */
import { inject, ref } from 'vue';
export default {
    name: "Tarea-Form",

    setup() {
        const tareas = inject('arregloTareas')
        const texto = ref('')
        const agregarTarea = () => {

            if (texto.value === '') {
                console.log('Uff, necesitas escribir algo')
                return
            }

            const tarea = {
                texto: texto.value,
                estado: false,
                id: Date.now()

            }

            tareas.value.push(tarea)
            texto.value = ''
        }

        return {
            agregarTarea,
            texto,
        }
    }

};
</script>