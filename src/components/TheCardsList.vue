<script>
    import {store, fetchImgSizes} from '../store';
    import TheCard from './TheCard.vue';
    export default{
        components: { TheCard },
        
        data(){
            return{
                store,
                imgSizes: [],
            }
        },
        mounted(){
            fetchImgSizes()
        }
    }
</script>

<template>
<h2>Film</h2>
    <div class="row">
        <div class="col col-sm-5 col-lg-3"
            v-for="(card, i) in store.movies">
            <TheCard 
            :card="card" 
            :key="i">
            </TheCard>
        </div>
    </div>

    <h2>Serie TV</h2>
    <div class="row">
        <div class="col col-sm-5 col-lg-3"
            v-for="card in store.seriesFormatted">
            <TheCard :card="card"></TheCard>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    @use '../styles/general.scss';
    @use '../styles/partials/_utilities.scss' as *;
    @use '../styles/partials/_variables.scss' as *;
    .row{
        @include flex_nowrap;
        margin-bottom: $standard_spacing;
        padding-block: $standard_spacing;
    }
</style>