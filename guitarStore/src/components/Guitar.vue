<script setup>



const props = defineProps({
    guitar: {
        type: Array,
        required: true
    }
})

defineEmits(['add-cart'])
</script>

<template>
    <div class="col-md-6 col-lg-4 my-4 row align-items-center">
        <div class="col-4">
            <img class="img-fluid" :src="'/img/' + guitar.imagen + '.jpg'" :alt="'imagen' + guitar.nombre">
        </div>
        <div class="col-8">
            <h3 class="text-black fs-4 fw-bold text-uppercase">{{ guitar.nombre }}</h3>
            <p>{{ guitar.description }}</p>
            <p class="fw-black text-primary fs-3">${{ guitar.precio }}</p>
            <button @click="$emit('add-cart',guitar)" type="button" class="btn btn-dark w-100 ">Agregar al Carrito</button>
        </div>
    </div><!-- FIN GUITARRA -->
</template>