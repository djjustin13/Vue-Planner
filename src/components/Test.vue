<template>
    <div class="test">
        <h1>{{title}}</h1>
        <input type="text" v-model="title">
        <p v-if="showName">{{user.firstName}}</p>
        <p v-text="user.lastName"></p>
        <ul>
            <li v-for="item in items" :key="item" v-text="item.title"></li>
        </ul>

        <button v-on:click="greet">say greeting</button>
        <br>
        <input type="text" v-on:keyup.enter="presskey">
        <hr>
        <label>Firstname: </label><input v-model="user.firstName" type="text">
        <label>Lastname: </label><input v-model="user.lastName" type="text">
        <h3>{{fullName}}</h3>

        <h3>{{msg}}</h3>
    </div>
</template>

<script>
    export default{
        name: 'Test',
        props: {
            msg:{
                type: String,
                default: 'Foobar'
            }
        },
        data(){
            return{
                title: 'Hello world',
                user:{
                    firstName: 'John',
                    lastName: 'Doe'
                },
                showName : false,
                items: [
                    {title: 'item1'},
                    {title: 'item2'},
                    {title: 'item3'},
                    {title: 'item4'}
                ]
            }
        },
        methods:{
            greet: function(){
                alert('hello');
            },
            presskey: function(e){
                console.log(e.target.value);
            }
        },
        computed:{
            fullName: function(){
                return this.user.firstName+' '+this.user.lastName;
            }
        }
    }
</script>

<style scoped>

</style>