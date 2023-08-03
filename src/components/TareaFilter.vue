<template>
    <div class="card mt-3">
        <div class="card-bod d-flex justify-content-between align-items-center">
            <span role="button" @click="filtrar('activos')">
                Activos
            </span>

            <span  role="button" @click="filtrar('todos')">
                Todos
            </span>

            <span role="button" @click="filtrar('completados')">
                Completados
            </span>
        </div>

    </div>
</template>

<script>
import { inject } from 'vue'
export default {
    name: "Tarea-Filter",
    setup() {
        const estado = inject('estado')
        const filtrar = valor => {
            estado.value = valor
        }
        return { filtrar }
    }
}
</script>

<style></style>