<template>
  <div id="app">
    <HeaderFlix @searching="starSearch" />
    <MainFlix :movies="movies" /> <!--aggiungo la variabile popolata dalla chiamata axios in un valore che passerò come props-->
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
    MainFlix
  },
  data(){
    return{
      movies: [],//torno array vuoto che verrà popolato dalla chiamata API
      api_key: 'fbf92bf5e34c88255fa295508c54019f', //key per API
    }
  },
  methods:{
    doSearchMovie(query){
      const params= {
        query: query,
        api_key: this.api_key
      }
      return axios.get(`https://api.themoviedb.org/3/search/movie`, { params }).then((response) => {
        this.movies = response.data.results; //salviamo nel nostro array vuoto la nostra chiamta ad axios
      });
    },
    starSearch(query){//filtra tra i movie
      this.doSearchMovie(query);
    }
  }
}
</script>

<style lang="scss">
  @import './style/general.scss';
  #app{
    width: 100%;
  }
</style>
