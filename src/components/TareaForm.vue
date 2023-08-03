<template>
    <form @submit.prevent="agregarTarea">
        <input type="text" maxlength="25" class="form-control my-3" placeholder="Ingrese tarea" v-model.trim="texto">
        <p v-if="mensajeError" class="alert alert-danger">{{ mensajeError }}</p>
    </form>
</template>
  
<script>
import { inject, ref } from 'vue';

export default {
    name: "Tarea-Form",

    setup() {
        const tareas = inject('arregloTareas');
        const texto = ref('');
        const mensajeError = ref('');

        const agregarTarea = () => {
            if (texto.value === '') {
                mostrarMensajeError('Uff, necesitas escribir algo');
                return;
            }

            // Verificar que esa tarea no exista (por el texto)
            const tareaExistente = tareas.value.find(tarea => tarea.texto === texto.value);
            if (tareaExistente) {
                mostrarMensajeError('La tarea ya existe');
                return;
            }

            const tarea = {
                texto: texto.value,
                estado: false,
                id: Date.now()
            };

            tareas.value.push(tarea);
            texto.value = '';
        };

        const mostrarMensajeError = (mensaje) => {
            mensajeError.value = mensaje;
            setTimeout(() => {
                mensajeError.value = '';
            }, 1500);
        };

        return {
            agregarTarea,
            texto,
            mensajeError,
        };
    },
};
</script>

  