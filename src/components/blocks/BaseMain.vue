<template>
    <main>
        <div class="container">
            <div class="row g-2">
                <h1>Film:</h1>
                <div class="col-12-4 col-md-4 col-lg-2" v-for="(cover,index) in dataShare.apiResponseMovie" :key="index">
                    <MovieCard :cover="cover"/>
                </div>
            </div>
            <div class="row">
                <h1>Serie Tv:</h1>
                <div class="col-12 col-md-4 col-lg-2" v-for="(cover,index) in dataShare.apiResponseSeries" :key="index">
                    <div class="prova-card p-2">
                        <img v-if="cover.poster_path == null" class="img-fluid" src="https://www.macitynet.it/wp-content/uploads/2016/06/Netflix740.jpg" alt="">
                        <img v-else class="img-fluid" :src="`https://image.tmdb.org/t/p/w780${cover.poster_path}`" alt="">
                        <p>{{cover.name}}</p>
                        <p>{{cover.original_name}}</p>
                        <p>{{cover.vote_average}}</p>
                        <flag :iso="cover.original_language" /> 
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import dataShare from '../../sharedfiles/dataShare';
import MovieCard from '../../components/commons/MovieCard'

export default {
    name: 'BaseMain',
    components: {
        MovieCard
    },
    data(){
        return{
            dataShare, 
            cover: {}
        }
    }
}
</script>

<style lang="scss" scoped>
    main{
        background-color: #A9A9A9;
        min-height: calc(100vh - 80px);
    }
</style>