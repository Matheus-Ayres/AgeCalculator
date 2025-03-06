<script setup>
import { ref } from 'vue';
import Insert from './components/Insert.vue';
import ResultAge from './components/ResultAge.vue';
import Confirm from  './components/Button.vue';

const birthDay = ref()
const birthMonth = ref()
const birthYear = ref()

const Day = ref()
const Month = ref()
const Year = ref()

const date = new Date();


function setBirthDay(a){
  birthDay.value = a
}

function setBirthMonth(a){
  birthMonth.value = a
}

function setBirthYear(a){
  birthYear.value = a
}

function calcDate() {
  const currentDay = date.getDate();
  const currentMonth = date.getMonth();
  const currentYear = date.getFullYear();

    Year.value = currentYear - birthYear.value;
    Month.value = (currentMonth - birthMonth.value) + 1;
    Day.value = currentDay - birthDay.value;
        
    if(Month.value <= 0){
      Year.value -= 1;
      Month.value += 12;
    }
    
    if (Day.value < 0){
      Month.value -= 1;
      Day.value += 30;
    }

    if (Year.value < 0){
      Year.value = 0
    }
}



</script>

<template>
  <body>
      <main>
        
        <div class="insert">
            <div class="a">
              <Insert @AgeInsert="setBirthDay" Date="Day" :MaxLength="2" :InvalidDay="birthDay"/>
            </div>
            <div class="a">
              <Insert @AgeInsert="setBirthMonth" Date="Month" :MaxLength="2" :InvalidMonth="birthMonth"/>
            </div>
            <div  class="a">
              <Insert  @AgeInsert="setBirthYear" Date="Year" :MaxLength="4" :InvalidYear="birthYear"/>
            </div>
          </div>

        <form @submit.prevent = "calcDate" class="button">
          <Confirm :VerifiDay="birthDay" :VerifiMonth="birthMonth" :VerifiYear="birthYear"/>
        </form>
          
        <div class="results">
          <div>
            <ResultAge v-if="Day == null" Calc = "- -" date="days"/>
            <ResultAge v-else :Calc = "Day" date="days"/>
          </div>
          <div>
            <ResultAge v-if="Month == null" Calc = "- -" date="months"/>
            <ResultAge v-else  :Calc = "Month" date="month"/>
          </div>
          <div>
            <ResultAge v-if="Year == null" Calc = " - -" date="years"/>
            <ResultAge v-else :Calc= "Year"  date="years"/>
          </div>
        </div>
        
      </main>

      
  </body>


</template>

<style scoped>
  main{
    background-color: white;
    margin: 50px 15px;
    border-radius: 10px 10px 80px 10px;
    padding: 55px 25px 15px 25px
  }

  .insert{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    text-transform: uppercase;
    letter-spacing: 3px;
    
  }

  .a{
    line-height: 1;
  }

  .mid-position{
    padding-bottom: 50px;
  }

  .results{
    padding-left: 25px;
  }
  .button{
    margin-bottom: 20px;
  }

  
</style>
