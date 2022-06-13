<template>
    <div class="movie-card">
        <img v-if="cover.poster_path == null" class="img-fluid" src="https://www.macitynet.it/wp-content/uploads/2016/06/Netflix740.jpg" alt="">
        <img v-else class="img-fluid" :src="`https://image.tmdb.org/t/p/w780${cover.poster_path}`" alt="">
        <div class="d-none">
            <p>{{cover.title}}</p>
            <p>{{cover.original_title}}</p>
            <p class="vote_stars">
                <span v-for="i in cover.vote_average" :key="i">
                <i class="fa-solid fa-star"></i>
                </span>
                <span v-for="index in (5 - cover.vote_average)" :key="index = 0">
                    <i class="fa-regular fa-star"></i>
                </span>
            </p>
            <flag :iso="cover.original_language" />
        </div>
    </div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {
        cover: Object
    }
}
</script>

<style lang="scss" scoped>
    .movie-card{
        height: 100%;
        border-radius: 5%;
        overflow: hidden;

        .vote_stars{
            color: rgb(240, 176, 0);
        }
    }
</style>