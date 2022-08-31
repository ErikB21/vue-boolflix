<template>
    <div class="list">
        <ul>
            <li>{{infoSerie.name}} -
                {{infoSerie.original_name}} -
                {{infoSerie.original_language}} -
                {{infoSerie.vote_average}}
            </li>    
        </ul>
    </div>
</template>

<script>
export default {
    name: 'CardFlixSerie',
    props:{
        infoSerie: Object//'infoSerie' rimanda un object ( ossia i singoli film compresi nell'array di oggetti filtrati)
    }
}
</script>

<style scoped lang="scss">
    
    
</style>