<template>
  <div id="app">
    <HeaderPage></HeaderPage>
    <MainContent></MainContent>

  </div>
</template>

<script>
import MainContent from './components/MainContent.vue'
import HeaderPage from './components/HeaderPage.vue'

export default {
  name: 'App',
  components: {
    HeaderPage,MainContent,
  }
}
</script>

<style lang="scss">
#app {
  max-height: 100vh;
}
</style>
