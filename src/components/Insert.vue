<script setup>
import { ref } from 'vue';

defineProps({
    Date: String,
    disabled: Boolean,
    InvalidDay: Number,
    InvalidMonth: Number,
    InvalidYear: Number,
})

const Age = ref()
const emit = defineEmits(['AgeInsert'])
const date = new Date();


function GetAge(){
    emit('AgeInsert',Age.value)
}

</script>

<template>
<div class="between">
    <div v-if="InvalidDay > 31 || InvalidMonth > 12 || InvalidYear > date.getFullYear()">
        <label class="InvalidLabel">{{ Date }}</label>
    </div>
    <div v-else>
        <label class="label">{{ Date }}</label>
    </div>
    
    <div v-if="InvalidDay > 31 || InvalidMonth > 12 || InvalidYear > date.getFullYear()" class="InvalidDiv">
        <input :disabled="disabled" p required @change="GetAge" v-model="Age" class="insertInvalid" type="text">
        <span class="Alert">
            Must Be a Valid {{ Date }}
        </span>
    </div>
    <div v-else>
        <input :disabled="disabled" required @change="GetAge" v-model="Age" class="insert" type="text">
    </div>
</div>
</template>

<style scoped>
    .insert{
        width: 60%;
        padding: 15px;
        font-weight: bold;
        border-radius: 10px;
        border: 1px solid rgb(156, 156, 156);
        height: 50%;
        font-size: 20px;
    }

    .insertInvalid{
        width: 60%;
        padding: 15px;
        font-weight: bold;
        border-radius: 10px;
        border: 1px solid red;
        height: 50%;
        font-size: 20px;
    }

    .between{
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: 80px;
    }

    .label{
        color: rgb(105, 105, 105);
        font-family: negri;
        font-size: 1rem;
    }

    .InvalidLabel{
        color: rgb(245, 39, 39);
        font-family: negri;
        font-size: 1rem;
    }

    .InvalidDiv{
        display: flex;
        flex-direction: column;
        padding-top: 10px;
    }

    .Alert{
        padding-top: 15px;
        font-family: invalid;
        letter-spacing: 0;
        color: red;
    }
</style>