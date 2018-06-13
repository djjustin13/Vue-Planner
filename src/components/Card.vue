<template>
    <div class="col-md-4 block">
        <div class="card">
            <div class="card-body">
                <h4 class="card-title">{{title}}</h4>
                <p class="card-text">{{text}}</p>

                <ul class="list-group list-group-flush">
                    <li class="list-group-item" v-for="(todo, index) in items" :key="`todo-${index}`" >
                        <input type="checkbox" class="toggle" v-model="todo.checked">
                        <span :class="{checked: todo.checked}">
                            {{todo.text}}
                            <a class="float-right" v-on:click="deleteitem(todo)"><i class="fas fa-times"></i></a>
                        </span>
                    </li>
                </ul>
            </div>
            <div class="card-footer white" :class="{'success-color': completed}">
                <!-- Default input -->
                <h5 class="white-text card-footer-text" v-if="completed"><i class="fas fa-check"></i> Gehaald</h5>
                <!-- <p class="white-text card-text" v-if="completed"><i class="fas fa-check"></i> Gehaald</p> -->
                <input v-else @keyup.enter="addItem" type="text" v-model="newItem.text" class="form-control" placeholder="Voeg item toe">
            </div>
        </div>
    </div>
</template>

<script>
    export default{
        name: 'Card',
        props: {
            title: {
                type: String,
                default: 'Building block'
            },
            text:{
                type: String,
                default: 'Lorem ipusm'
            },
            items:{
                type: Array,
                default: ()=> []
            }
        },data(){
            return{
                newItem:{},
                completed: false,
            }
        },
        methods:{
            addItem: function(e){
                if(this.newItem.text)
                this.items.push({
                    text: this.newItem.text,
                    checked: false
                });
                this.newItem = {}
                e.preventDefault();
            },
            deleteitem: function(item){
                this.items.splice(this.items.indexOf(item), 1)
            }
        },
        watch: {
            items: {
                handler: function (after, before) {
                    let vals = true
                    after.forEach(function(el){
                        if(el.checked == false) vals = false
                    })

                   this.completed = vals
                },
                deep: true
            }
        }
    }
</script>

<style scoped>
    .block{
        padding: 0.75rem;
    }
    .checked{
        text-decoration: line-through;

    }
    .card{
        transition: box-shadow .25s;
    }

    .card-footer-text{
        padding: .75rem 1.25rem;
        margin-bottom: 0;
    }

    .card:hover{
        box-shadow: 0 8px 17px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
    }
</style>