<template>
    <main>

    </main>
</template>

<script>
import axios from 'axios';
import dataShare from '../../sharedfiles/dataShare';


export default {
    name: 'BaseMain',
    data(){
        return{
            dataShare, 
            
        }
    },
    methods: {
        getApiResponse(){
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: 'b12c3d5dea05d54fe7ab668775bb5103',
                    query: 'star'
                }
            })
            .then((response)=> {
                this.apiResponse = response.data.results
                console.log(response.data.results)
            })
            .catch((error)=> {
                console.log(error);
            })
        }
    }
}
</script>

<style lang="scss" scoped>
    main{
        background-color: #A9A9A9;
        height: calc(100vh - 80px);
    }
</style>