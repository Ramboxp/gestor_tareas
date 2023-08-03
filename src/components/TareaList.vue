<template>
  <ul class="list-group">
    <TareaItem v-for="tarea in tareas" :key="tarea.id" :tarea="tarea" />
  </ul>
</template>

<script>

import { inject } from 'vue'
import TareaItem from './TareaItem.vue'

export default {
  name: 'Tarea-List',

  components: {
    TareaItem
  },

  setup() {
    const tareas = inject('arregloTareas')
    return { tareas }
  },

  data() {
    return {

    }
  },

}
</script>