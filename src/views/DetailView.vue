<template>
    <section id="main">
        <div class="container">
            <div class="row">
                <div class="col-4 col-12-medium">

                    <!-- Sidebar -->
                    <section class="box">
                        <header>
                            <h3>Infos</h3>
                        </header>
                        <p> amiiboSeries: <b>{{currentanimes.amiiboSeries}}</b> <br />
                            character: {{currentanimes.character}}<br />
                            gameSeries: {{currentanimes.gameSeries}}<br />
                            type: {{currentanimes.type}}
                        </p>

                    </section>
                    <section class="box">
                        <header>
                            <h3>Dates sorties</h3>
                        </header>

                        <ul class="divided">
                            <li>au:{{currentanimes.release}}// ne passe pas (release.au) </li>
                            <li>eu: {{currentanimes.release}}//ne passe pas (release.eu)</li>
                            <li></li>
                            <li></li>
                        </ul>

                    </section>

                </div>
                <div class="col-8 col-12-medium imp-medium">

                    <!-- Content -->
                    <article class="box post">
                        <a href="#" class="featured"><img
                                :src="currentanimes.image"
                                alt="" /></a>
                        <header>
                            <h2>{{currentanimes.name}}</h2>
                            <p>{{currentanimes.type}}</p>
                        </header>



                    </article>

                </div>
            </div>
        </div>
    </section>
</template>
<script setup>
import {ref,onMounted} from 'vue'
import {useRoute} from "vue-router"
import axios from 'axios'

const AMIBO_API = 'https://www.amiiboapi.com/api/amiibo'

const route = useRoute()

const currentanimes = ref({})


const {tailId} = route.params 




onMounted(async () => {
    const {data} = await axios.get(`${AMIBO_API}/?tail=${tailId}`)
    currentanimes.value = data.amiibo[0]
    
})
    

</script>