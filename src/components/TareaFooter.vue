<template>
    <li class="list-group-item d-flex justify-content-between align-items-center">
        <span role="button">
            Cantidad: {{ contarActivos }}
        </span>
        <span role="button" @click="eliminaCompletados">
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
            return tareas.value.filter(item => item.estado === false).length
        })
        const eliminaCompletados = () => {
            tareas.value = tareas.value.filter(item => item.estado === false)
        }
        return { contarActivos, eliminaCompletados }
    },
}
</script>

<style></style>