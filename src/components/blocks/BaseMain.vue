<template>
    <main>
        <div class="container">
            <div class="row">
                <div class="col-12 col-md-4 col-lg-2" v-for="(cover,index) in dataShare.apiResponse" :key="index">
                    <div class="prova-card">
                        <p>{{cover.title}}</p>
                        <p>{{cover.original_title}}</p>
                        <p>{{cover.original_language}}</p>
                        <p>{{cover.vote_average}}</p>
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
        height: calc(100vh - 80px);
    }

    .prova-card{
        border: 1px solid black;
    }
</style>