<template>
  <div class="main-content">
    <div class="container">
      <label class="fs-5 text-white" for="filtro">Filtra per genere: </label>
      <select
        class="select-genre"
        :class="{ show: cards.length >= counted }"
        v-model="selectedOption"
        name="filtro"
        id="filtro-genere"
      >
        <option value="">All</option>
        <option v-for="genere in genderFinded" :key="genere" :value="genere">
          {{ genere }}
        </option>
      </select>
      <div class="row row-cols-5">
        <div class="col" v-for="(card, i) in filteredCard" :key="i">
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
  props: {
    searchText: String,
  },
  data() {
    return {
      pageLoaded: true,
      cards: [],
      genderFinded: [],
      counted: null,
      selectedOption: "",
      
    };
  },
  computed: {
    filteredCard() {
        if(this.searchText){
             return this.cards.filter((element) => {
            return element.genre.includes(this.selectedOption) && (element.title.toLowerCase().includes(this.searchText.toLowerCase()) || element.author.toLowerCase().includes(this.searchText.toLowerCase()));
      });
        }else {
            return this.cards.filter((element) => {
            return  element.genre.includes(this.selectedOption)

            });
        }
        
    },
    
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((axiosResp) => {
        const cardData = axiosResp.data.response;
        this.counted = axiosResp.data.response.length;
        this.cards = cardData;

        this.cards.forEach((element) => {
          if (!this.genderFinded.includes(element.genre)) {
            this.genderFinded.push(element.genre);
          }
        });
        this.$emit("pageLoading", this.pageLoaded);
      })
  },
  
};
</script>

<style lang="scss">
.main-content {
  overflow: auto;
  flex-grow: 1;
  background-color: #1e2d3b;
  padding-top: 5rem;
  padding-bottom: 5rem;
}
.select-genre {
  padding: 1rem 0.75rem;
  margin-bottom: 2rem;
  width: calc(100% / 5);
  background-color: #1bd760;
  font-weight: bold;
  font-size: 1.2rem;
}
</style>