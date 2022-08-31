<template>
    <div>
        <i class="fa-solid fa-star" v-for="index in voteStar" :key="index"></i>
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
    i{
        color: yellow;
        padding-left: 3px;
        margin-left: 3px;
    }
</style>