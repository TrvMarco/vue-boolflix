<template>
  <header class="container-fluid">  
    <BoolflixLogo class="header_logo"/>
    <SearchBar/>
  </header>
</template>

<script>
import SearchBar from '../../components/commons/SearchBar'
import BoolflixLogo from '../../components/commons/BoolflixLogo'

export default {
    name: 'BaseHeader',
    components: {
        SearchBar,
        BoolflixLogo
    } 
}
</script>

<style lang="scss" scoped>
  header{
    height: 5rem;
    background-color: #000;
    display: flex;
    justify-content: space-between;
    align-items: center;

  }

  .header_logo{
    height: 3.125rem;
  }
</style>