<!-- TareaForm.vue -->
<template>
    <form @submit.prevent="agregarTarea">

        <div class="mb-3">
            <input type="text" class="form-control" id="tarea" aria-describedby="tarea" placeholder="Ingrese tarea">
        </div>
    </form>
</template>
  
<script>
import { inject } from 'vue';
export default {
    name: "Tarea-Form",
    setup() {
        const arrayTareas = inject('arregloTareas')

        const agregarTarea = () => { 
        
        } 

        return {
            agregarTarea
        }
    }

};
</script>