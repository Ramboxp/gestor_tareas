<template>
    <li class="list-group-item d-flex justify-content-between align-items-center">
        <span v-bind:class="{ 'incorrecto': tarea.estado }" role="button" @click="cambiaEstado(tarea.id)">
                {{ tarea.texto }}
        </span>
        <span role="button" @click="borrar(tarea.id)">
            <i class="fa-solid fa-xmark"></i>
        </span>
    </li>
</template>
  
<script>
/* eslint-disable */
import { inject } from 'vue'
export default {
    name: 'Tarea-Item',

    props: {
        tarea: {
            type: Object,
            required: true
        }
    },
    setup() {
        const tareas = inject('arregloTareas')
        const borrar = id => {
            tareas.value = tareas.value.filter(item => item.id !== id)
        }
        const cambiaEstado = id => {
            tareas.value = tareas.value.map(item => {
                if (item.id === id) {
                    item.estado = !item.estado; // Aquí alternamos el estado entre true y false
                }
                return item
            })
        }
        return { borrar, cambiaEstado }
    }
}
</script>

<style>
.incorrecto {
    text-decoration: line-through;
    color: rgb(255, 64, 0);
}
</style>