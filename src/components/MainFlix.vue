<template>
  <main>
    <div class="container">
        <CardFlix v-for="movie in movies" :type="'movie'" :key='movie.id' :info="movie"/>
    </div>
  </main>
</template>

<script> 
import CardFlix from './CardFlix.vue';
export default {
    name: "MainFlix",
    components: { 
        CardFlix
    },
    props:{
        movies: Array,//importo i dati da App.vue e li passo con un ciclo v-for
    }
}
    
</script>

<style scoped lang="scss">
    main{
        width: 100%;
        height: 100%;
        background-color: rgb(48, 48, 122);
        .container{
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: space-evenly;
            flex-wrap: wrap;
        }
    }
</style>