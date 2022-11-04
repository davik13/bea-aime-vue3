<script setup>
import Banner from '../components/Banner.vue';
import Intro from '../components/Intro.vue';
import Footer from '../components/Footer.vue';


</script>

<template>
  <main id="page-wrapper">
    <section id="header">
      <h1><a href="index.html">AmiiVue</a></h1>
      <nav id="nav">
        <RouterLink :tag="li" :active-class="current" to="/">Home</RouterLink>
        <RouterLink class="current" to="/animes">Liste anime</RouterLink>
      </nav>
      <Banner />
      <Intro />
    </section>
    <Footer />

  </main>
</template>
