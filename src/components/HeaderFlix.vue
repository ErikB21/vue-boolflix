<template>
    <header>
        <nav>
            <input v-model="keySearch" @keyup.enter="searchKey" type="text" placeholder="Cerca e spera che funzioni..."/>
            <button @click="searchKey" type="button">Cerca</button>

            <!--aggiungo v-model ad input con valore 'keySearch', che sarà il titolo dei film filtrati -> 
                con @searching passo al padre (HeaderFlix) in App.vue l'evento da scatenare -->
            <!-- il $emit passa dal figlio (HeaderFlix) al padre (App.vue) il dato e aggancia due parametri:
            il nome dell'avento (searching) che passa al padre e il valore passato dall'input tramite v-model 'keySearch'-->
        </nav>
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
        padding-right: 3rem;
        background-color: black;
        nav{
            padding: 2rem 0;
            display: flex;
            justify-content: end;
            align-items: center;
            input{
                padding: 0.5rem 0;
                width: 20rem;
                margin: 0 1rem;
            }
            button{
                padding: 0.5rem 1.5rem;
            }
        }
    }
</style>