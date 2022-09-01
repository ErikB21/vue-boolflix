<template>
    <main>
        <div class="cinema">
            <h2 v-if="movies.length > 0">FILM</h2>
            <div class="cardlist marg-bot">
                <CardFlix class="eb_marg" v-for="movie in movies"  :key='movie.id' :img="movie" :info="movie" :vote="voto" /><!--ciclo for nell'array movies, e info come props per passare i valori al figlio card-->
            </div>
        </div> 
        <div class="cinema">
            <h2 v-if="series.length > 0">SERIE TV</h2>
            <div class="cardlist marg-bot">
                <CardFlixSerie class="eb_marg" v-for="serie in series"  :key='serie.id' :img="serie" :infoSerie="serie" :vote="voto" /><!--ciclo for nell'array series, e info come props per passare i valori al figlio card-->
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
    CardFlixSerie,
},
    props:{
        movies: Array,//importo i dati da App.vue e li passo con un ciclo v-for
        series: Array, //importo i dati da App.vue e li passo con un ciclo v-for
    },
    
}
    
</script>

<style scoped lang="scss">
    main{
        padding-top: 150px;
        height: 87vh;
        width: min((100% - 3rem),1200px);
        margin-inline: auto;
        display: flex;
        align-items: center;
        flex-direction: column;
        
        .cinema{
            display: flex;
            flex-direction: column;
            h2{
                color: mediumaquamarine;
                text-align: center;
                padding: 20px 0;
                font-size: 4rem;
                font-family: "Bungee shade", sans-serif;
            }
            .cardlist{
                display: flex;
                flex-wrap: wrap;
                justify-content: center;
                
                
                .eb_marg{
                    margin: 20px 5px;
                }
                
            }
        }
    }
</style>