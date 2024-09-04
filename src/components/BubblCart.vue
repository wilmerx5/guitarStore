<script setup>

const props= defineProps({
    quantity:{
        type:Number,
        required:true
    }
})
</script>

<template>
<p v-if="quantity<1" id="quantity" ></p>
<p v-else-if="quantity>9" id="quantity" >9+</p>
<p v-else="quantity>9" id="quantity" >{{quantity}}</p>



</template>

<style>
#quantity{
    background-color: red;
    color: white;
    border-radius: 50%;
    text-align: center;
    position: absolute;
    margin: 0;
    width: 65%  ;
    top: 10px  ;

}
</style>