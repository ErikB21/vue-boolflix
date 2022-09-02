<template>
    <div>
        <i class="fa-star " v-for="n in 5" :key="n" :class="n > voteStar? 'fa-regular' : 'fa-solid'"></i>
    </div>
</template>

<script>
export default {
    name: 'StarFlix',
    props:{
        vote: Number
    },
    computed:{
        voteStar(){//mi permette di avere un calcolo da 1 a 5
            const vote = Math.round(this.vote / 2);
            return vote;
        }
    }
}
</script>

<style scoped lang="scss">
    .fa-solid{
        color: yellow;
        padding-left: 3px;
        margin-left: 3px;
    }
    .fa-regular{
        color: white;
        padding-left: 3px;
        margin-left: 3px;
    }
</style>