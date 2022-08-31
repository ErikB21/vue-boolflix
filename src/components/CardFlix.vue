<template>
    <div class="card">
        <h2>{{info.title}}</h2>
        <h3>{{info.original_title}}</h3>
        <div><span>{{info.original_language}}</span></div>
        <div class="vote">{{info.vote_average}}</div>    
    </div>
</template>

<script>
export default {
    name: 'CardFlix',
    props:{
        info: Object,//'info' rimanda un object ( ossia i singoli films compresi nell'array di oggetti filtrati
    }
}
</script>

<style scoped lang="scss">
    .card{
        width: calc(100% / 5 - 70px);
        margin: 0 35px;
        height: 350px;
        padding: 10px 0;
        border: 1px solid white;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
        text-align: center;
        h2{
            padding: 10px 0;
            color: gainsboro;
        }
        span{
            font-size: 1.2rem;
            color: greenyellow;
        }
        .vote{
            color: beige;
        }

    }
</style>