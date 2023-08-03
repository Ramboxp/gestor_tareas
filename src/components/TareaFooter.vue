<template>
    <li class="list-group-item d-flex justify-content-between align-items-center">
        <span role="button">
           {{ contarActivos }}
        </span>
        <span role="button">
                Eliminar completados
        </span>
    </li>
</template>

<script>
import { computed, inject } from 'vue'
export default {

    name: "Tarea-Footer",

    setup() {
        const tareas = inject('arregloTareas')
        const contarActivos = computed(() => { 
            return tareas.value.filter( item => item.estado === false).length
        })
    return { contarActivos }
  },
}
</script>

<style></style>