<template>
    <div class="col-md-6 col-lg-4 block">
        <div class="card">
            <div class="card-body">
                <div class="buttons float-right">
                    <i class="fas fa-undo-alt icon" @click="resetData"></i>
                </div>
                <h4 class="card-title">{{title}}</h4>
                <p class="card-text">{{text}}</p>

                <ul class="list-group list-group-flush">
                    <li class="list-group-item" v-for="(todo, index) in items" :key="`todo-${index}`" :class="[todo.category]">
                        <input type="checkbox" class="toggle" v-model="todo.checked">
                        <span :class="{checked: todo.checked}">
                            {{todo.text}}
                            <a class="float-right" v-on:click="deleteitem(todo)"><i class="fas fa-times"></i></a>
                        </span>
                    </li>
                </ul>
            </div>
            <div class="card-footer white" :class="{'success-color': completed}">
                <h5 class="white-text card-footer-text" v-if="completed"><i class="fas fa-check"></i> Gehaald</h5>
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
                completed: false
            }
        },
        created: function() {
            localStorage.setItem("original_"+this.title, JSON.stringify(this.items));
            let data = localStorage.getItem(this.title);
            if (data){
                let object = JSON.parse(data);
                this.items = object;
            }
            
        },
        methods:{
            addItem: function(e){
                if(this.newItem.text)
                this.items.push({
                    text: this.newItem.text,
                    checked: false,
                    category: 'default'
                });
                this.newItem = {}
                e.preventDefault();
            },
            deleteitem: function(item){
                this.items.splice(this.items.indexOf(item), 1);
            },
            save: function(){
                localStorage.setItem(this.title, JSON.stringify(this.items));
            },
            resetData: function(){
                let data = localStorage.getItem("original_"+this.title);
                let object = JSON.parse(data);
                this.items = object;
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

                   this.save()
                },
                deep: true
            }
        }
    }
</script>

<style scoped>
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