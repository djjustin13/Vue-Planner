<template>
    <div class="page">
        <nav class="navbar navbar-expand-lg navbar-dark hr-color">
            <a class="navbar-brand" href="#">Building Block Planner</a>
            <ul class="nav float-right" style="position: absolute; right: 10px">
                <li class="nav-item" ><a class="nav-link" href="#" data-toggle="modal" data-target="#info" style="color: #FFFF"><i class="fas fa-question"></i></a></li>
            </ul>

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

        <div class="modal fade" id="info" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">BB-Planner info</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <h5>Opslaan:</h5>
                <p>
                    Alle wijzigingen die je doet aan jouw to-do lijstjes worden direct lokaal opgeslagen. Wanneer je een lijst terug wilt zetten naar de originele staat kun je de reset knop gebruiken.
                </p>
                <hr>
                <h5>Updates:</h5>
                <p>
                    Updates van deze tool worden automatisch uitgerold. Omdat jouw to-do lijsten lokaal worden opgeslagen kan je nog niet direct volledig gebruik maken van deze update. Je moet daarom handmatig de nieuwe content updaten. Dit zal op de homepage aangegeven worden wanneer er een update is.
                </p>
                <hr>
                <h5>Legenda:</h5>
                <span class="legende important">Extra belangrijke onderdelen</span> <span class="legende">Normale onderdelen</span> <span class="legende extra">Extra onderdelen</span>
                <hr>
                <h5>Disclamer</h5>
                <p>
                    Let op, BB-Planner is een tool ontwikkeld voor en door studenten. De standaard onderdelen op de lijsten zijn slechts een indicatie van de taken die je zou kunnen doen om je building blocks te halen. Bij een assesment gaat het vooral om de beargumentatie en je totale verhaal. Zorg daarom dat je voldoende kennis hebt van het onderwerp.
                </p>
                <hr>
                <h5>Feedback & vragen:</h5>
                <p>
                    Voor vragen over bepaalde onderdelen van buildingblocks kun je terecht bij peercoaches of docenten. Heb je vragen over de tool of feedback om deze te verbeteren? <a href="mailto:info@justinderuiter.nl">Stuur een mailtje ;)</a>
                </p>
                <hr>
                <small>Justin de Ruiter & Peercoaches 2018</small>
            </div>
            </div>
        </div>
        </div>
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
    base: 'vue-planner',
    routes:[
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
