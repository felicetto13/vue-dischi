
<template>
  <header>
    <div class="my-navbar">
      <img
        src="../../public/img/spotify-logo-png-7053.png"
        alt="logo spotify"
      />
      <div class="search-bar">
        <input type="text" id="searched-bar" @keyup="$emit('searchDisk', textSearchBar)" v-model="textSearchBar" />
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderPage",
  data(){
      return {
          textSearchBar: undefined
      } 
  },
};
</script>

<style lang="scss" scoped>
.my-navbar {
  background-color: #2d3a46;
  padding: 0.5rem;
  flex-shrink: 0;
  display: flex;

  img {
    background-color: transparent;
    width: 4rem;
  }
    .search-bar {
    align-self: center;
    flex-grow: 1;
    padding: 0 2rem;

        input[type="text"]{
            width: 100%;
            border-radius: 10px;
            border-color: transparent;
        }
  }
}
</style>