<template>
  <header class="container-fluid">  
        <div class="input-group">
            <input type="text" class="form-control" placeholder="Cerca un titolo" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="dataShare.searchInputValue">
            <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="getApiResponse()"><i class="fa-solid fa-magnifying-glass"></i></button>
        </div>
  </header>
</template>

<script>
import axios from 'axios';
import dataShare from '../../sharedfiles/dataShare'

export default {
    name: 'BaseHeader',
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
                }
            })
            .then((response)=> {
                this.dataShare.apiResponse = response.data.results
            })
            .catch((error)=> {
                console.log(error);
            })
        }
    }

}
</script>

<style lang="scss" scoped>
    header{
        height: 5rem;
        background-color: #000;
        display: flex;
        justify-content: flex-end;
        .input-group{
            width: 20%;
            align-self: flex-start;
            align-self: center;
        }
    }
</style>