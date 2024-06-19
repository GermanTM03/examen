<template>
    <div class="Contenedor">
        <p>Número total de Productos: {{ proyectosCompletadas }}</p>
                <p>Número de Productos completadas: {{ totalProyectos }}</p>
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Nombre</th>
                    <th>Cantidad</th>
                    <th>Categoria</th>
                    <th>Completado</th>
                
                </tr>
            </thead>
            <tbody>
                <tr v-for="proyecto in Productos" :key="proyecto.id">
                    <td>{{ proyecto.id }}</td>
                    <td>{{ proyecto.name }}</td>
                    <td>{{ proyecto.quantity }}</td>
                    <td>{{ proyecto.category }}</td>
                    <td>{{ proyecto.completed}}</td>
                    <td class="acciones">
                        <button @click="marcarComoCompletado(proyecto)" class="completado">{{ proyecto.completed ? 'Completado' : 'Terminar' }}</button>
                        <button @click="eliminarEntrada(proyecto.id)" class="eliminar">Eliminar</button>
                    </td>
                </tr>
            </tbody>
        </table>
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Nombre</th>
                    <th>Cantidad</th>
                    <th>Categoria</th>
                    <th>Completado</th>
                
                </tr>
            </thead>
            <tbody>
                <tr v-for="proyecto in Productos" :key="proyecto.id">
                    <td>{{ proyecto.id }}</td>
                    <td>{{ proyecto.name }}</td>
                    <td>{{ proyecto.quantity }}</td>
                    <td>{{ proyecto.category }}</td>
                    <td>{{ proyecto.completed}}</td>
                    <td class="acciones">
                        <button @click="marcarComoCompletado(proyecto)" class="completado">{{ proyecto.completed ? 'Completado' : 'Terminar' }}</button>
                        <button @click="eliminarEntrada(proyecto.id)" class="eliminar">Eliminar</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script setup lang="ts">
import type { IProductos } from './Interfaces/InterProductos';
import ObjectProductos from './Data/DataProyecto'
import { ref, defineEmits, computed } from 'vue'

const Productos = ref<IProductos[]>(ObjectProductos);


const totalProyectos = computed(() => Productos.value.length);


const proyectosCompletadas = computed(() => Productos.value.filter(Productos => Productos.completed).length);

const emit = defineEmits(['Eliminar', 'Completar']);

const eliminarEntrada = (id: number) => {
    Productos.value = Productos.value.filter(   Productos => Productos.id !== id);
    emit('Eliminar', id);
};

const marcarComoCompletado = (proyectos: IProductos) => {
    proyectos.completed = !proyectos.completed;
    emit('Completar', 'Terminar');
};
</script>


<style scoped>

</style>./Interfaces/InterProductos./Interfaces/InterProductos