<script setup>
defineProps({
    date: String,
    Calc: String
})



</script>

<template>
    <div class="pad">
        <span class="trait">{{ Calc }}</span>
        <span class="date">{{ date }}</span>
    </div>

</template>

<style scoped>
    .trait{
        font-family: calc;
        padding-right: 10px;
        font-size: 3rem;
        color: blueviolet;
    }

    .date{
        font-family: calc;
        font-size: 3.5rem;
    }

</style>