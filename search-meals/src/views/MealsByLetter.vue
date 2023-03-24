<template>
    <div class="flex gap-2 justify-center mt-2">
        <router-link :to="{ name: 'byLetter', params: { letter } }" v-for="letter of letters" :key="letter">
            {{ letter }}
        </router-link>
    </div>

  <Meals :meals="meals"/>

</template>


<script setup>
import store from '../store';
import {computed} from '@vue/reactivity'
import { useRoute } from 'vue-router';
import { onMounted,watch } from 'vue';
import MealItem from '../components/MealItem.vue';
import Meals from '../components/Meals.vue'


const route=useRoute();
const letters='ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");
const meals =computed(()=>store.state.mealsByLetter)


//Harflerin üzerine tıkladıgım zaman gelen menüler bu watch fonk sayesinde 
watch(route, ()=> {
    store.dispatch('searchMealsByLetter',route.params.letter)
})


onMounted(()=>{
    store.dispatch('searchMealsByLetter',route.params.letter)
})


</script>