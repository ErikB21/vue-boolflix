<template>
    <div class="card">
        <div class="img">
            <img :src="getPoster(info.poster_path)" :alt="info.title"><!--richiamo il metodo che ciclerà le foto in base al film-->
        </div>
        <div class="border-out">
            <div class="description">
                <span><strong>Titolo</strong><br>{{info.title}}</span> 
                <span><strong>Titolo originale</strong><br>{{info.original_title}}</span>
                <span class="img-flag"><strong>Lingua</strong><br><img class="flag" v-if="flag.includes(info.original_language)" :src="require('../assets/' + info.original_language + '.png')" :alt="info.original_language"/></span>
                <span><strong>Voto</strong><br> <StarFlix :vote="info.vote_average" /></span>
                <p><span><strong>Overview</strong><br></span><br>{{info.overview}}</p>
            </div>
        </div><!--aggiungo il componente StarFlix dove gli passerò il voto ciclato, ma come risultato ci saranno le stelle-->
    </div>
</template>





<script>
import StarFlix from './StarFlix.vue';
export default {
    name: "CardFlix",
    props: {
        info: Object, //'info' rimanda un object ( ossia i singoli film compresi nell'array di oggetti filtrati)
    },
    data(){
        return{
            flag: ['ca','it', 'en', 'fr', 'es', 'da', 'ja', 'ko', 'nl','no', 'pt', 'ro', 'ru', 'sv', 'zh'],//add ogni bandiera che ci serve
        }
    },
    methods: {
        getPoster(path) {
            if (path === null) {
                return "https://i.imgur.com/h8qvbqj.png";
            } //altrimenti ritorna sito/path (path sarà la nostra img che ci ritorna le foto ciclate in base al film o serie richiesta)
            return `https://image.tmdb.org/t/p/w342/${path}`;
        }
    },
    components: { StarFlix }
}
</script>

<style scoped lang="scss">
    @import '../style/utilities.scss';//importo lo stile della card
    
</style>