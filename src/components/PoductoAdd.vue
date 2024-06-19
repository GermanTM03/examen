<template>
    <slot name="header"></slot>
    <div class="Contenedor">
        <div class="Formulario">
            <form @submit.prevent="Ingreso">
                <h1>Productos</h1>
                <label for="name" class="label">Nombre:</label>
                <input type="text" v-model="name" placeholder="">
                <p v-if="name.length > 15" class="error">El nombre no puede tener más de 15 caracteres.</p>

                <label for="quantity" class="label">Cantidad:</label>
                <input type="int" v-model="quantity" placeholder="">
                <p v-if="quantity.length > 15" class="error">El nombre no puede tener más de 15 caracteres.</p>

                <label for="category" class="label">Categoria:</label>
                <input type="text" v-model="category" placeholder="">
                <p v-if="category.length > 15" >El nombre no puede tener más de 15 caracteres.</p>

            
             
              
            </form>
            <form @submit.prevent="Ingresso">
                <h1>Productos</h1>
                <label for="name" class="label">Nombre:</label>
                <input type="text" v-model="name" placeholder="">
                <p v-if="name.length > 15" class="error">El nombre no puede tener más de 15 caracteres.</p>

                <label for="quantity" class="label">Cantidad:</label>
                <input type="int" v-model="quantity" placeholder="">
                <p v-if="quantity.length > 15" class="error">El nombre no puede tener más de 15 caracteres.</p>

                <label for="category" class="label">Categoria:</label>
                <input type="text" v-model="category" placeholder="">
                <p v-if="category.length > 15" >El nombre no puede tener más de 15 caracteres.</p>

            
             
              
            </form>
        </div>
    </div>
</template>

<script setup lang="ts">
import type { IProductos } from './Interfaces/InterProductos';
import ObjectPoductos from './Data/DataProyecto'
import { ref, computed } from 'vue'

const name = ref('')
const quantity = ref('')
const category = ref('')
const completed = ref('')

const Products = ref<IProductos[]>(ObjectPoductos);

const formularioValido = computed(() => {
    return name.value.length > 0 && name.value.length <= 15 &&
    quantity.value.length > 0 && quantity.value.length <= 20 &&
    category.value.length > 0 && category.value.length <= 50 &&
         
});

const Ingreso = () => {
    if (!formularioValido.value) {
        alert('Por favor, completa todos los campos correctamente.');
        return;
    }

    if (Products.value.some((producto) => producto.name === name.value)) {
        alert('El Producto esta registrado')
        return;
    }

    const NewProyecto: IProductos = {
        id: ObjectPoductos.length + 1,
        name: name.value,
        quantity: quantity.value,
        category: category.value,
        completed: false
    }

    Products.value.push(NewProyecto)
    alert("Producto agregado")

    name.value = ''
    quantity.value = ''
    category.value = ''
    completed.value = ''
}
</script>

<style scoped>

    


</style>