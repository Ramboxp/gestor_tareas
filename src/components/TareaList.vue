<template>
  <ul class="list-group">
    <TareaItem v-for="tarea in tareas" :key="tarea.id" :tarea="tarea" />
    
    <li v-if="tareas.length === 0" class="list-group-item" >
      No hay tareas
    </li>

    <TareaFooter v-if="tareas.length > 0"/>

  </ul>
</template>

<script>
import { inject } from 'vue'
import TareaItem from './TareaItem.vue'
import TareaFooter from './TareaFooter.vue'

export default {
  name: 'Tarea-List',

  components: {
    TareaItem,
    TareaFooter

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