    <template>
        <div class="mt-3 mb-3">
            <div class="card-body d-flex justify-content-between align-items-center">

                <button type="button" class="btn btn-success" role="button" @click="filtrar('activos')">
                    Activos
                </button>

                <button type="button" class="btn btn-primary" role="button"  @click="filtrar('todos')">
                    Todos
                </button>

                <button type="button" class="btn btn-secondary" role="button" @click="filtrar('completados')">
                    Completados
                </button>
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
