<script setup>

const props= defineProps({
    quantity:{
        type:Number,
        required:true
    }
})
</script>

<template>
<p v-if="quantity>9" id="quantity" >9+</p>
<p v-if="quantity<=9" id="quantity" >{{quantity}}</p>


</template>

<style>
#quantity{
    background-color: red;
    color: white;
    border-radius: 50%;
    text-align: center;
    position: relative;
    margin: 0;
    width: 10% I !important;
    top: 10px !important ;

}
</style>