<template>
    <div class="card">
        <div class="img">
            <img :src="getPoster(infoSerie.poster_path)" :alt="infoSerie.name"><!--richiamo il metodo che ciclerà le foto in base al serie-->
        </div>
        <div class="border-out">
            <div class="description">
                <span><strong>Titolo</strong><br>{{infoSerie.name}}</span>
                <span><strong>Titolo originale</strong><br>{{infoSerie.original_name}}</span>
                <span class="img-flag"><strong>Lingua</strong><br><img class="flag" v-if="flag.includes(infoSerie.original_language)" :src="require('../assets/' + infoSerie.original_language + '.png')" :alt="infoSerie.original_language"/></span>
                <span><strong>Voto</strong><br> <StarFlix :vote="infoSerie.vote_average" /></span>
                <p><span><strong>Overview</strong></span><br>{{infoSerie.overview}}</p>
            </div>
        </div><!--aggiungo il componente StarFlix dove gli passerò il voto ciclato, ma come risultato ci saranno le stelle-->
    </div>
</template>

<script>
import StarFlix from './StarFlix.vue';
export default {
    name: 'CardFlixSerie',
    props:{
        infoSerie: Object,//'infoSerie' rimanda un object ( ossia i singoli film compresi nell'array di oggetti filtrati)
    },
    data(){
        return{
            flag: ['ca','it', 'en', 'fr', 'es', 'da', 'ja', 'ko', 'nl','no', 'pt', 'ro', 'ru', 'sv', 'zh'],//add ogni bandiera che ci serve
        }
    },
    methods:{
        getPoster(path){//se il nostro parametro path è null, ritorna 404
            if(path === null){
                return 'https://i.imgur.com/h8qvbqj.png'
            }//altrimenti ritorna sito/path (path sarà la nostra img che ci ritorna le foto ciclate in base al film o serie richiesta)       
            return `https://image.tmdb.org/t/p/original/${path}`;
        }
    },
    components: { StarFlix }
}
</script>

<style scoped lang="scss">
    @import '../style/utilities.scss';
</style>