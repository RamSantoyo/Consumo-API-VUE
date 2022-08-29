<script setup>
    const props = defineProps(["inicio", "fin", "post"]);
</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button type="button" class="btn btn-outline-primary" @click="$emit('disminuircontador')"
        :disabled="inicio <= 0 ? true : false">
        regresar a los - {{inicio}}</button>
        <button type="button" class="btn btn-outline-primary" @click="$emit('aumentarcontador')"
        :disabled="fin >= post.length ? true : false">        
        siguiente - pagina:{{fin}}</button>
    </div>
</template>

<style scoped>

</style>