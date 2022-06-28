<template>
  <div id="app">
    <LoaderPage :loadingState="statemantLoading"></LoaderPage>
    <HeaderPage @searchDisk="searchDisk"></HeaderPage>
    <MainContent :searchText="searchedDisk" @pageLoading="pageLoad"></MainContent>

  </div>
</template>

<script>
import MainContent from './components/MainContent.vue'
import HeaderPage from './components/HeaderPage.vue'
import LoaderPage from './components/LoaderPage.vue'

export default {
  name: 'App',
  components: {
    HeaderPage,MainContent,
    LoaderPage,
  },
  data(){
    return{
      statemantLoading: false,
      searchedDisk: "",
    }
  },
  methods:
  {
    pageLoad(statement){
      this.statemantLoading = statement;
    },
    searchDisk(text){
      this.searchedDisk = text;
    }
  }
}
</script>

<style lang="scss">
#app {
  
  height: 100vh;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}
</style>
