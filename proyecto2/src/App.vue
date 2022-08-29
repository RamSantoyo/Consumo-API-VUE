<script setup>

import contenedor from './components/icons/seccion.vue';
import paginacion from './components/icons/paginacion.vue';
import carga from './components/icons/loading.vue';
import { onMounted, ref } from 'vue'; // importar la referencia de vue


//paginacion
const elementos = 5;
let inicio = ref(0);
let fin = ref(elementos);;

const aumentarcontador = () => {
  inicio.value += elementos;
  fin.value += elementos;
}

const disminuircontador = () => {
  inicio.value -= elementos;
  fin.value -= elementos;
}

//loading
const loading = ref(true);

//api 
let post = ref([]); //variable intercativa para guardar los datos del api

onMounted( async() => { //cuando se cargue la pagina se ejecuta el codigo
  try {
    const url = await fetch('https://jsonplaceholder.typicode.com/posts');
    const data = await url.json();
    post.value = data; //se guarda los datos en la variable intercativa
  } catch (error) {
    return error;
  } finally{
    setTimeout(() => { //para que se cargue el loading despues de 2 segundos
      loading.value = false;
    }, 2000);
  }
});


//funcion para atrapar numero
  let numero = ref('');//variable intercativa para guardar el numero de la seccion
  const seleccionarid = (item) =>{
    numero.value = item; //asignamos el valor de la variable item a la variable numero
  }

</script>

<template>
      <carga v-if="loading"></carga>
      <div v-else>
        <div class="container">
          <h1>ID Seleccionado: {{numero}}</h1>
          <paginacion @aumentarcontador="aumentarcontador" @disminuircontador="disminuircontador"
          :inicio="inicio" :fin="fin" :post="post"></paginacion>
        </div>           
        <contenedor v-for="item in post.slice(inicio, fin)"  :key="item.id" 
        :id="item.id" :title="item.title" :body="item.body"
        @seleccionarid="seleccionarid">
        </contenedor><!--recorre el arreglo de post y lo muestra en el contenedor, despues pasamos los parametros a la funcion seleccionarid-->
      </div>
</template>


<style scoped>


</style>