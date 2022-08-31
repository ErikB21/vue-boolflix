<template>
    <div class="list">
        <ul>
            <li>{{info.title}} -
                {{info.original_title}} -
                {{info.original_language}} -
                {{info.vote_average}}
            </li>    
        </ul>
    </div>
</template>

<script>
export default {
    name: 'CardFlix',
    props:{
        info: Object,//'info' rimanda un object ( ossia i singoli film compresi nell'array di oggetti filtrati)
    }
}
</script>

<style scoped lang="scss">
    
    
</style>