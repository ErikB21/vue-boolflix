<template>
    <div class="card">
        <div class="img">
            <img :src="getPoster(infoSerie.poster_path)" :alt="infoSerie.name"><!--richiamo il metodo che ciclerà le foto in base al serie-->
        </div>
        <h2>{{infoSerie.name}}</h2>
        <h5>{{infoSerie.original_name}}</h5>
        <div class="lingua">
            {{infoSerie.original_language}}
        </div>
        <div class="voto">
            {{infoSerie.vote_average}}
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardFlixSerie',
    props:{
        infoSerie: Object,//'infoSerie' rimanda un object ( ossia i singoli film compresi nell'array di oggetti filtrati)
    },
    methods:{
        getPoster(path){//se il nostro parametro path è null, ritorna 404
            if(path === null){
                return 'https://i.imgur.com/h8qvbqj.png'
            }//altrimenti ritorna sito/path (path sarà la nostra img che ci ritorna le foto ciclate in base al film o serie richiesta)       
            return `https://image.tmdb.org/t/p/original/${path}`;
        }
    }
}
</script>

<style scoped lang="scss">
    @import '../style/utilities.scss';
</style>