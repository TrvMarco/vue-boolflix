<template>
    <div class="movie-card">
        <div class="cover_image">
            <img v-if="serieCover.poster_path == null" class="img-fluid" src="https://www.macitynet.it/wp-content/uploads/2016/06/Netflix740.jpg" alt="">
            <img v-else class="img-fluid" :src="`https://image.tmdb.org/t/p/w780${serieCover.poster_path}`" alt="">
        </div>
        <div class="card_description p-2">
            <p>{{`Titolo: ${serieCover.name}`}}</p>
            <p>{{`Titolo Originale: ${serieCover.original_name}`}}</p>
            <p class="vote_stars">
                <span v-for="i in serieCover.vote_average" :key="i">
                <i class="fa-solid fa-star"></i>
                </span>
                <span v-for="i in (5 - serieCover.vote_average)" :key="i">
                    <i class="fa-regular fa-star"></i>
                </span>
            </p>
            <p v-if="serieCover.overview === '' ">{{`Trama non disponibile`}}</p>
            <p v-else>{{`Trama: ${serieCover.overview}`}}</p>
            <flag :iso="serieCover.original_language" />
        </div>
    </div>
</template>

<script>
export default {
    name: 'SerieCard',
    props: {
        serieCover: Object,
    }
}
</script>

<style lang="scss" scoped>
    .movie-card{
        position: relative;
        overflow: hidden;
        transition: 0.5s;
        height: 18.75rem;
        object-fit: center;

        .vote_stars{
            color: rgb(240, 176, 0);
        }

    }
    .cover_image{
        position: relative;
        border-radius: .3125rem;
        overflow: hidden;
        height: 100%;

        img{
            object-fit: cover;
        }
    }

    .card_description{
        border-radius: 5%;
        font-size: small;
        color: #fff;
        height: 100%;
        display: block;
        position: absolute;
        bottom: 0;
        width: 100%;
        background-color: rgba($color: #000000, $alpha: 0.7);
        overflow: auto;
        opacity: 0;
    }

    .movie-card:hover .card_description{
        opacity: 1;
    }

    .movie-card:hover{
        transform: scale(1.05);
    }
</style>