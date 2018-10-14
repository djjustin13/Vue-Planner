<template>
    <div class="cards">
        <div v-if="!isHidden" class="row">
            <div class="col block">
                <div class="card">
                    <span class="icon closeButton" v-on:click="isHidden = true"><i class="fas fa-times"></i></span>
                    <div class="row card-body">
                        <div class="col-md-8">
                            <h4>Update info</h4>
                            <p>
                                We hebben gemerkt dat veel 1e jaars studenten gebruik maken van deze tool en hebben daarom een grote update uitgebracht. Omdat jouw to-do lijsten lokaal worden opgeslagen kan je nog niet direct volledig gebruik maken van deze update. Wanneer je update worden al jouw lijstjes gereset! Wanneer je nog geen lijsten in gebruik had, ben je automatisch up to date. <a href="#" @click="resetAll">Update nu!</a>
                            </p>
                            <hr>
                            <h5>Legenda:</h5>
                            <span class="legende important">Extra belangrijke onderdelen</span> <span class="legende">Normale onderdelen</span> <span class="legende extra">Extra onderdelen</span>
                        </div>
                        <div class="col-md-4">
                            <h4>Disclamer</h4>
                            <p>
                                Let op, BB-Planner is een tool ontwikkeld voor en door studenten. De standaard onderdelen op de lijsten zijn slechts een indicatie van de taken die je zou kunnen doen om je building blocks te halen. 
                            </p>
                        </div>
                    </div>
                </div>
                
            </div>
        </div>
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
                cards: [],
                isHidden: false
            }

        },
        methods:{
            resetAll: function(){
                localStorage.clear();
                location.reload();
            }
        },
        created: function(){
            let vueapp = this;
            $.getJSON('static/data.json', function(json){
               vueapp.cards = json
            });
            
        }
    }
</script>

<style>
    .block{
        padding: 0.75rem;
    }

    .legende{
        padding: 12px 20px;
        border-radius: 4px;
        border: 1px solid #dfdfdf;
        display: inline-block;
        margin: 5px;
    }
    .important{
        background-color: #ffbc0085;
    }
    .extra{
        background-color: #07ce0754;
    }

    .closeButton{
        position: absolute;
        right: 23px;
        top: 15px;
    }

    .icon{
        color:rgb(170, 170, 170);
        z-index: 10;
        font-size: 16px;
    }

    .icon:hover{
       color:rgb(134, 134, 134);
       transform: scale(1.1, 1.1);
    }
</style>