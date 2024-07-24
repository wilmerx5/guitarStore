<script setup>
import { onMounted, ref, watch } from 'vue';
import Footer from './components/Footer.vue';
import Guitar from './components/Guitar.vue';
import Header from './components/Header.vue';
import { db } from './data/data';

const guitars = ref([])
const cart = ref([])
const mainGuitar = ref({})

onMounted(() => {
    console.log("component ready")
    guitars.value = db
    mainGuitar.value=db[3]


    let savedCart = localStorage.getItem('cart')

    if(savedCart){
        cart.value=JSON.parse(savedCart)
    }

   
})

watch(cart,()=>{
saveCartLocalStore()
},{
deep:true
})

const addCart = (guitar) => {
    const alreadyExist = cart.value.findIndex(p => p.id == guitar.id)

    if (alreadyExist == -1) {

        cart.value.push({ cantidad: 1, ...guitar })
    }
    else {
        cart.value[alreadyExist].cantidad++
    }
    console.log(cart.value)
}

const lessOne = (guitar) => {
    const index = cart.value.findIndex(p => p.id == guitar.id)

    cart.value[index].cantidad == 1 ? '': cart.value[index].cantidad--



}

const addOne = (guitar) => {
    const index = cart.value.findIndex(p => p.id == guitar.id)

    cart.value[index].cantidad++
}

const deleteItem=(guitar)=>{

    cart.value= cart.value.filter((e)=>e.id!=guitar.id)
   

}

const saveCartLocalStore=()=>{

    localStorage.setItem('cart',JSON.stringify(cart.value))
}
const cleanCart=()=>{
    cart.value=[]
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
        @less-one="lessOne" 
        @add-one="addOne"
        :mainGuitar=mainGuitar
        @add-cart="addCart"
        @delete-item="deleteItem"
        @clean-cart="cleanCart"
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
