<template>
    <ul class="list-group-item d-flex justify-content-between align-items-center">
        <span role="button">
            {{ tarea.texto }}
        </span>
        <span role="button" @click="borrar(tarea.id)">
            <i class="fa-solid fa-xmark"></i>
        </span>
    </ul>
</template>
  
<script>
/* eslint-disable */
import { inject } from 'vue'
export default {
    name: 'Tarea-List',
    props: {
        tarea: {
            type: Object,
            required: true
        }
    },
    setup() {
        const tareas = inject('arregloTareas')
        
        const borrar = id => {
            tareas.value = tareas.value.filter( item => item.id !== id )
        }

        return { borrar }
    }
}
</script>