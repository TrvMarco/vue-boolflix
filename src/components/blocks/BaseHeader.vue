<template>
  <header class="container-fluid">  
    <SearchBar/>
  </header>
</template>

<script>
import SearchBar from '../../components/commons/SearchBar'

export default {
    name: 'BaseHeader',
    components: {
        SearchBar,
    } 
}
</script>

<style lang="scss" scoped>
    header{
        height: 5rem;
        background-color: #000;
        display: flex;
        justify-content: flex-end;
    }
</style>