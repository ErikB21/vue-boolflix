<template>
  <main>
    <div class="container">
        <h2>FILM</h2>
        <div class="film">
            <CardFlix v-for="movie in movies"  :key='movie.id' :img="movie" :info="movie"/><!--ciclo for nell'array movies, e info come props per passare i valori al figlio card-->
        </div>
        <h2>SERIE TV</h2>
        <div class="serie">
            <CardFlixSerie v-for="serie in series"  :key='serie.id' :img="serie" :infoSerie="serie"/><!--ciclo for nell'array series, e info come props per passare i valori al figlio card-->
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
        series: Array, //importo i dati da App.vue e li passo con un ciclo v-for
    }
}
    
</script>

<style scoped lang="scss">
    .container{
        width: 100%;
        display: flex;
        align-items: center;
        flex-direction: column;
        .film, .serie{
            display: flex;
            flex-wrap: wrap;
            justify-content: space-evenly;
        }
    }
</style>