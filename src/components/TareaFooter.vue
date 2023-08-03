<template>
        <div class="mt-3 mb-3">
    <li class="card-body d-flex justify-content-between align-items-center">
        <span role="button">
            Activos: {{ contarActivos }}
        </span>
        <button type="button" class="btn btn-danger" role="button" @click="eliminaCompletados">
            Eliminar completados
        </button>
    </li>
</div>
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