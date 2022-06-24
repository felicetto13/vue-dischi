<template>
  <div class="main-content">
    <div class="container">
        <select :class="{'show':cards.length >= counted}" name="filtro" id="filtro-genere">
            <option v-for="genere in genderFinded" :key="genere" :value="genere">{{ genere }}</option>
        </select>
      <div class="row row-cols-5">
        <div class="col" v-for="(card, i) in cards" :key="i">
          <CardElement :card-element="card"></CardElement>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import CardElement from "./CardElement.vue";
export default {
  components: { CardElement },
  name: "MainContent",
  data() {
    return {
      cards: [],
      genderFinded: [],
      counted: null 
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((axiosResp) => {
        const cardData = axiosResp.data.response;
        this.counted = axiosResp.data.response.length
        this.cards = cardData;
      });
      setTimeout(() => {
          this.cards.forEach((element) =>{
              if(!this.genderFinded.includes(element.genre)){
                this.genderFinded.push(element.genre)
              }
              })
      }, 3000) 
      
  },
  methods:
  {
      
  }
};
</script>

<style lang="scss">
.main-content {
  height: 100%;
  background-color: #1e2d3b;
  padding-top: 5rem;
  padding-bottom: 5rem;
}
</style>