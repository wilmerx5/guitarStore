<script setup>
import { onMounted, ref } from 'vue';
import Footer from './components/Footer.vue';
import Guitar from './components/Guitar.vue';
import Header from './components/Header.vue';
import { db } from './data/data';

const guitars = ref([])
const cart = ref([])

onMounted(() => {
    console.log("component ready")
    guitars.value = db
})


const addCart = (guitar) => {
    cart.value.push(guitar)
    console.log(cart.value)
}
</script>


<template>

    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>GuitarLA</title>
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;700;900&display=swap" rel="stylesheet">
        <link rel="stylesheet" href="./src/style.css">
    </head>

    <body>
        <Header
        :cart="cart"
        />

        <main class="container-xl mt-5">
            <h2 class="text-center">Nuestra Colección</h2>

            <div class="row mt-5">

                <Guitar :guitar="guitar" @add-cart="addCart" v-for="guitar in guitars" />


            </div>
        </main>

        <Footer></Footer>

    </body>

</template>

