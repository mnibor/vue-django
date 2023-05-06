<template>
    <section class="mt-5 text-center mx-auto">
        <h1 class="text-danger">Panadería y Rotisería Carlitos</h1>
        <img class="img-fluid" :src="require('@/assets/img/fondo.png')" alt="">
        <div class="mt-3">
            <button type="button" class="btn btn-info">Categoría 1</button>
            <button type="button" class="btn btn-info">Categoría 2</button>
            <button type="button" class="btn btn-info">Categoría 3</button>
            <button type="button" class="btn btn-info">Categoría 4</button>
        </div>
        <hr>
    </section>
</template>

<script>
    export default {
        name: 'NavigationComponent'
    }
</script>

<style>
    /* Estilos adicionales del Navigation */
</style>