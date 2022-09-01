<template>
  <div class="kenburns-top" id="app">
    <HeaderFlix @searching="starSearch" />
    <MainFlix :movies="movies" :series="series" /> <!--aggiungo la variabile popolata dalla chiamata axios in un valore che passerò come props-->
  </div>
</template>

<script>
import HeaderFlix from './components/HeaderFlix.vue';
import MainFlix from './components/MainFlix.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HeaderFlix,
    MainFlix,
},
  data(){
    return{
      movies: [],//torno array vuoto che verrà popolato dalla chiamata API con i film
      api_key: 'fbf92bf5e34c88255fa295508c54019f', //key per API,
      series: [],//torno array vuoto che verrà popolato da chiamta Api con le serie tv
      loadFlix: true
    }
  },
  methods:{
    doSearchMovieAndSeries(query){
      const params= {
        query: query,
        api_key: this.api_key,
        lang: 'it-IT'
      }

      axios.get(`https://api.themoviedb.org/3/search/movie`, { params }).then(response => {
        this.movies = response.data.results; //salviamo nel nostro array vuoto la nostra chiamta ad axios per i film
      })
      .catch(err =>{
        console.log(err);
      })

      axios.get(`https://api.themoviedb.org/3/search/tv`, {params}).then(response =>{
        this.series = response.data.results; //salviamo nell'array vuoto la chiamata ad axios per le serie tv
      })
      .catch(err =>{
        console.log(err);
      })
      
      
    },
    starSearch(query){//filtra tra i movie e le serie
      this.doSearchMovieAndSeries(query);
    }
  }
}
</script>

<style lang="scss">
  @import './style/general.scss';
  #app{
    width: 100%;
    height: 100vh;
    overflow-y: auto;
    background-repeat: no-repeat;
    background-image: url(./assets/rick.jpg);
    background-size: cover;
    @import './style/animationApp.scss';
  }
  
</style>
