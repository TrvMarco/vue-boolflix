<template>
  <div class="input-group search-bar">
            <input type="text" class="form-control" placeholder="Cerca un titolo" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="dataShare.searchInputValue">
            <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="getApiResponse()"><i class="fa-solid fa-magnifying-glass"></i></button>
        </div>
</template>

<script>

import axios from 'axios';
import dataShare from '../../sharedfiles/dataShare'

export default {
    name: 'SearchBar',
    data(){
        return{
            dataShare,
        }
    },
    methods:{
        getApiResponse(){
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: 'b12c3d5dea05d54fe7ab668775bb5103',
                    query: this.dataShare.searchInputValue,
                    language: 'it-IT',
                }
            })
            .then((response)=> {
                response.data.results.forEach(element => {
                    if(element.original_language == "en"){
                        element.original_language = "gb"
                    }else if(element.original_language == "ja"){
                        element.original_language = "jp"
                    }
                });

                response.data.results.forEach(element => {
                    element.vote_average = Math.ceil(element.vote_average / 2)
                })
                this.dataShare.apiResponseMovie = response.data.results

            })
            .catch((error)=> {
                console.log(error);
            })

            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: 'b12c3d5dea05d54fe7ab668775bb5103',
                    query: this.dataShare.searchInputValue,
                    language: 'it-IT',
                }
            })
            .then((response)=> {
                response.data.results.forEach(element => {
                    if(element.original_language == "en"){
                        element.original_language = "gb"
                    }else if(element.original_language == "ja"){
                        element.original_language = "jp"
                    }

                    response.data.results.forEach(element => {
                    element.vote_average = Math.ceil(element.vote_average / 2)
                    })
                    this.dataShare.apiResponseMovie = response.data.results
                });
                this.dataShare.apiResponseSeries = response.data.results
            })
            .catch((error)=> {
                console.log(error);
            })

            this.dataShare.searchInputValue = ""
        }
    } 
}
</script>

<style lang="scss" scoped>
    .search-bar{
            width: 250px;
            align-self: flex-start;
            align-self: center;
    }
</style>