<template>
  <div id="app">
    <LoaderPage></LoaderPage>
    <HeaderPage></HeaderPage>
    <MainContent></MainContent>

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
  }
}
</script>

<style lang="scss">
#app {
  max-height: 100vh;
}
</style>
