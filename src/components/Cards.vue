<template>
    <div class="cards">
        <div class="row">
        <Card v-for="(card, index) in cards" :key="`card-${index}`" :title="card.title" :text="card.text" :items="card.todos"/>
    </div>
    </div>
    
</template>

<script>
import data from '../assets/data.json'
import Card from './Card'

    export default{
        name: 'Cards',
        components:{
            Card
        },
        data(){
            return{
                cards: []
            }

        },
        created: function(){
            this.cards = data
        }
    }
</script>

<style scoped>

</style>