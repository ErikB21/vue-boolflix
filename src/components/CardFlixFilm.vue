<template>
    <div class="card">
        <div class="img">
            <img :src="getPoster(info.poster_path)" :alt="info.title"><!--richiamo il metodo che ciclerà le foto in base al film-->
        </div>
        <h2>{{info.title}}</h2>
        <h5>{{info.original_title}}</h5>
        <div class="lingua">
            {{info.original_language}}
        </div>
        <div class="voto">
            {{info.vote_average}}
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardFlix',
    props:{
        info: Object,//'info' rimanda un object ( ossia i singoli film compresi nell'array di oggetti filtrati)
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
    @import '../style/utilities.scss';//importo lo stile della card
</style>