<template>
    <header>
        <div class="logo">
            <img src="../assets/Senza titolo.png" alt="">
        </div>
        <div class="cerca">
            <input v-model="keySearch" @keyup.enter="searchKey" type="text" placeholder="Cerca e spera che funzioni..."/>
            <button @click="searchKey" type="button">Cerca</button>
        </div>
            
            <!--aggiungo v-model ad input con valore 'keySearch', che sarà il titolo dei film e serie filtrati -> 
                con @searching passo al padre (HeaderFlix) in App.vue l'evento da scatenare -->
            <!-- il $emit passa dal figlio (HeaderFlix) al padre (App.vue) il dato e aggancia due parametri:
            il nome dell'avento (searching) che passa al padre e il valore passato dall'input tramite v-model 'keySearch'-->
    </header>
</template>

<script>
export default {
    name: 'HeaderFlix',
    data(){
        return{
            keySearch: '', //variabile vuota, dinamica in base a cosa cercheremo
        }
    },
    methods:{
        searchKey(){
            this.$emit('searching', this.keySearch); //emettiamo ad App.vue la variabile contente la ricerca effettuata
        }
    }
}
</script>

<style scoped lang="scss">
    header{
        width: 100%;
        height: 13vh;
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: black;
        position: fixed;
        top: 0;
        left: 0;
        z-index: 999;
        padding: 0 20px;
        .logo{
            width: 130px;
            img{
                width: 100%;
            }
        }
        input{
            padding: 0.5rem 0;
            width: 15rem;
            margin: 0 1rem;
        }
        button{
            padding: 0.5rem 1.5rem;
        }
    }
</style>