<script setup>
    const props = defineProps(["id", "title", "body"]);
</script>

<template>
<div class="container">
    <div class="card mt-4">
        <div class="card-body p-4">
            <h1>{{id}}</h1>
            <h5 class="card-title">{{title}}</h5>
            <p>{{body}}</p>
            <button class="btn btn-primary" @click="$emit('seleccionarid', id)">Atrapar id</button>
        </div>
    </div>
</div>
    
</template>

<style scoped>

  .rojo{
    color: red;
  }
  .azul{
    color: blue;
  }
  .verde{
    color: green;
  }
</style>