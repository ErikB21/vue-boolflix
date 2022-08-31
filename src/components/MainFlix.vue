<template>
  <main>
    <div class="container">
        <div class="film">
            <CardFlix v-for="movie in movies"  :key='movie.id' :info="movie"/><!--ciclo for nell'array movies, e info come props per passare i valori al figlio card-->
        </div>
        <div class="serie">
            <CardFlixSerie v-for="serie in series"  :key='serie.id' :infoSerie="serie"/><!--ciclo for nell'array series, e info come props per passare i valori al figlio card-->
        </div>
    </div>
  </main>
</template>

<script> 
import CardFlix from './CardFlixFilm.vue';
import CardFlixSerie from './CardFlixSerie.vue';
export default {
    name: "MainFlix",
    components: {
    CardFlix,
    CardFlixSerie
},
    props:{
        movies: Array,//importo i dati da App.vue e li passo con un ciclo v-for
        series: Array //importo i dati da App.vue e li passo con un ciclo v-for
    }
}
    
</script>

<style scoped lang="scss">
    
</style>