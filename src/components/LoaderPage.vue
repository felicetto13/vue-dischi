<template>
  <div class="loader" :class="{ hidden: loadingState == true}">
    <div class="spinner-border text-success" role="status">
      <span class="visually-hidden">Loading...</span>
    </div>
  </div>
</template>

<script>
export default {
    props:
    {
        loadingState: Boolean
    },
};
</script>

<style lang="scss" scoped>
.loader {
    position: relative;
    height: 100vh;
    display: flex;
    flex-grow: 1;
    flex-shrink: 0;
    background-color: #1e2d3b;
    align-content: center;
    justify-content: center;
    align-items: center;
    transition: all .5s ease;
}

.hidden {
    transition: all .5s ease;
    display: none;
}
</style>