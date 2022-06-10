<template>
    <main>
        <div class="container">
            <div class="row">
                <h1>Film:</h1>
                <div class="col-12 col-md-4 col-lg-2" v-for="(cover,index) in dataShare.apiResponseMovie" :key="index">
                    <div class="prova-card p-2">
                        <img v-if="cover.poster_path == null" class="img-fluid" src="https://www.macitynet.it/wp-content/uploads/2016/06/Netflix740.jpg" alt="">
                        <img v-else class="img-fluid" :src="`https://image.tmdb.org/t/p/w780${cover.poster_path}`" alt="">
                        <p>{{cover.title}}</p>
                        <p>{{cover.original_title}}</p>
                        <span v-for="i in cover.vote_average" :key="i">
                            <i class="fa-solid fa-star"></i>
                        </span>
                        <p>{{cover.vote_average}}</p>
                        <flag :iso="cover.original_language" /> 
                    </div>
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

export default {
    name: 'BaseMain',
    data(){
        return{
            dataShare, 
        }
    }
}
</script>

<style lang="scss" scoped>
    main{
        background-color: #A9A9A9;
        min-height: calc(100vh - 80px);
    }

    .prova-card{
        height: 100%;
        border: 1px solid black;
    }
</style>