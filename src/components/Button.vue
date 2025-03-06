<script setup>
defineProps({
    VerifiDay: Number,
    VerifiMonth: Number,
    VerifiYear: Number
})

const date = new Date();


</script>





<template>
    <div class="w-100">
        <img v-if="VerifiDay = null|| VerifiDay > 31 || VerifiMonth == null || VerifiMonth > 12 || VerifiYear == null || VerifiYear > date.getFullYear()" class="arrowFalse" src="../../public/icon-arrow.svg">
        <button v-else> <img class="arrowTrue" src="../../public/icon-arrow.svg"> </button>

        
    </div><hr>
</template>

<style scoped>
    .w-100{
    position: relative;
    top: 35px;
    width: 100%;    
    display: flex;
    justify-content: center;
    align-items: center;
    }

    button{
    border: none;
    border-radius: 100%;

    }

    hr{
    color: rgb(105, 105, 105);;

    }

    .arrowFalse{
    height: auto;
    background-color: rgb(175, 165, 184);
    width: 28px;
    height: 28px; 
    padding: 20px;
    border-radius: 100%;

    }

    .arrowTrue{
    height: auto;
    background-color: blueviolet;
    width: 28px;
    height: 28px; 
    padding: 20px;
    border-radius: 100%;
    }

    @media (max-width: 669px){
        .w-100{
            justify-content:flex-end;

        }
    }

</style>