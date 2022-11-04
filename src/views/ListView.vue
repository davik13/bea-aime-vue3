<template>
    <section id="main">
        <div class="container">
            <section id="header">
                <h1><a href="index.html">AmiiVue</a></h1>
                <nav id="nav">
                    <RouterLink :tag="li" :active-class="current" to="/">Home</RouterLink>
                    <RouterLink class="current" to="/animes">Liste anime</RouterLink>
                </nav>
            </section>
            <!-- Content -->
            <article class="box post">

                <header>
                    <h2>Ma Collection</h2>
                    <p>(ici le nombre d'amiibo)</p>
                </header>
                <p>
                <table>
                    <tr>
                        <th>Character</th>
                        <th>game Series</th>
                        <th>Action</th>
                    </tr>
                    <tr v-for="anime in animes">
                        <td>{{ anime.character }}</td>
                        <td>{{ anime.gameSeries }}</td>
                        <td><button @click="goAnimes(anime.tail)">voir</button></td>
                    </tr>
                </table>
                </p>

            </article>

        </div>
    </section>
</template>
<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'
import { useRouter } from 'vue-router'

const animes = ref([])
const router = useRouter()

onMounted(async () => {
    const allanime = await axios.get('https://www.amiiboapi.com/api/amiibo/')
    animes.value = allanime.data.amiibo
})

const goAnimes = tailId => {
    // console.log({moviesId})
    const routeOptions = {
        name: 'animesDetails',
        params: {
            tailId: tailId
        }
    }

    router.push(routeOptions)
}


</script>