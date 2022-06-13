<template>
    <main>
        <div class="container">
            <div class="row g-2">
                <h2 class="text-uppercase font-weight-bold">BoolFlix films</h2>
                <div class="col-6 col-md-4 col-lg-2" v-for="(cover,index) in dataShare.apiResponseMovie" :key="index">
                    <MovieCard :cover="cover"/>
                </div>
            </div>
            <div class="row">
                <h2 class="text-uppercase font-weight-bold">BoolFlix series</h2>
                <div class="col-12 col-md-4 col-lg-2" v-for="(scover,index) in dataShare.apiResponseSeries" :key="index">
                    <SerieCard :serieCover="scover"/>
                </div>
            </div>
        </div>
    </main>
</template>

<script>

import dataShare from '../../sharedfiles/dataShare';
import MovieCard from '../../components/commons/MovieCard'
import SerieCard from '../../components/commons/SerieCard'

export default {
    name: 'BaseMain',
    components: {
        MovieCard,
        SerieCard
    },
    data(){
        return{
            dataShare, 
            cover: {},
            serieCover: {}
        }
    }
}
</script>

<style lang="scss" scoped>
    main{
        background-color: #272727;
        min-height: calc(100vh - 80px);
        color: #fff;
    }
</style>