<template>
  <div>
    <div class="card">
      <img :src="cardElement.poster" :alt="cardElement.author" />
      <div class="card-body">
        <div class="card-title">{{ cardElement.title }}</div>
        <div class="card-author">{{ cardElement.author }}</div>
        <div class="card-year">{{ cardElement.year }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardElement",
  props: {
    cardElement: Object,
  },
};
</script>

<style lang="scss" scoped>
.card {
  margin-bottom: 2rem;
  background-color: #2d3a46;
  color: white;
  text-align: center;
  font-size: .9rem;  
    img {
    width: 100%;
    aspect-ratio: 1;
    object-fit: cover;
  }
}
</style>