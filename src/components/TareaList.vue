<template>
  <ul class="list-group">
    <TareaItem v-for="tarea in tareas" :key="tarea.id" :tarea="tarea" />

    <li v-if="tareas.length === 0" class="list-group-item">
      No hay tareas
    </li>

    <TareaFooter v-if="tareas.length > 0" />
    <TareaFilter />

  </ul>
</template>

<script>
 /* eslint-disable */
import { computed, inject, provide, ref } from 'vue'
import TareaItem from './TareaItem.vue'
import TareaFooter from './TareaFooter.vue'
import TareaFilter from './TareaFilter.vue'

export default {
  name: 'Tarea-List',

  components: {
    TareaItem,
    TareaFooter,
    TareaFilter
  },

  setup() {
    const tareasTareas = inject('arregloTareas')

    const estado = ref('todos')

    const tareas = computed(() => {

      if (estado.value === 'todos') {
        return tareasTareas.value
      }
      if (estado.value === 'activos') {
        return tareasTareas.value.filter(item => item.estado === false)
      }
      if (estado.value === 'completados') {
        return tareasTareas.value.filter(item => item.estado === true)
      }

    })

    provide('estado', estado)
    return { tareas, tareasTareas }




  },

  data() {
    return {

    }
  },

}
</script>