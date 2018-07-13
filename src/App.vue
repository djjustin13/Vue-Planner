<template>
    <div class="page">
        <nav class="navbar navbar-expand-lg navbar-dark hr-color">
            <a class="navbar-brand" href="#">Building block To-do's</a>
            <!-- <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false"
                aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
            </button> -->
            <!-- <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <router-link class="nav-link" to="/">Home</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link class="nav-link" to="/test">Test</router-link>
                    </li>
                </ul>
            </div> -->
        </nav>
        <div class="container main">
            <router-view></router-view>
        </div>
        <footer class="page-footer font-small hr-color">
            <div class="footer-copyright text-center py-3">© 2018 Copyright:
                <a href="#"> Justin de Ruiter</a>
            </div>
        </footer>
    </div>
</template>

<script>
import Vue from 'vue'
import VueRouter from 'vue-router'
import Users from './components/Users'
import Test from './components/Test'
import Cards from './components/Cards'


Vue.use(VueRouter)

const router = new VueRouter({
    mode: 'history',
    base: __dirname,
    routes:[
        {path:'/vue-planner', component: Cards},
        {path:'/', component: Cards},
        // {path:'/test', component:Test}
    ]
})

export default{
    name: 'App',
    router
}
</script>

<style>
body{
    background-color: #EFEFEF;
}
i{
    font-family: font-awesome;
}
.main.container{
    margin-top: 25px;
}
.hr-color{
    background-color: #C40038 !important;
}

</style>
