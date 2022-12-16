<script>
    import { store } from '../store';
    export default{
        props: {
            card: {
                type: Object
            },
        },
        methods: {
            getMovieSrc(path){
                if (!path){
                    return "src/assets/No_Image_Available.jpg";
                }
                return "https://image.tmdb.org/t/p/" + store.imgSizes[3] + path;
            },
        },
    }
</script>

<template>
    <div class="card">
        <img v-if="card.poster_path == null" src="https://picsum.photos/185/282" alt="">
        <img v-else :src="getMovieSrc(card.poster_path)" class="card-img-top" :alt="card.title">
        <div class="card-body">
            <h5 class="card-title">{{card.title}}</h5>
            <p class="card-text">{{card.original_title}}</p>
            <ul class="list-group list-group-flush">
                <li class="list-group-item">{{card.original_language}}</li>
                <li class="list-group-item">{{card.vote_average}}</li>
            </ul>
        </div>
    </div>
</template>

<style>

</style>