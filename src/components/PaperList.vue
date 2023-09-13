<script>
import axios from "axios";
import BaseSelect from "./BaseSelect.vue";

export default {
  data() {
    return {
      apiUri: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
      arrayCardsPlay: [],
      countInsideArray: 0,
    
    };
  },

  methods: {
    fetchCarte(endpoint) {
      axios.get(endpoint).then((response) => {
        this.arrayCardsPlay = response.data.data;
      });
    },

 
  },
  components:{BaseSelect},

  created() {
    this.fetchCarte(this.apiUri);
   
  },
};
</script>

<template>

  <div
    class="card-img"
    v-for="(lista, index) in this.arrayCardsPlay"
    :key="lista.id"
  >
    <img :src="lista.card_images[this.countInsideArray].image_url" alt="" />
    <div class="text-center">
      <p>{{ lista.name.toUpperCase() }}</p>
      <p>{{ lista.archetype }}</p>    

    </div>
  </div>
  


</template>

<style lang="scss" scoped>
@use "../assets/scss/partials/variables" as *;

.card-img {
  width: 200px;
  height: 380px;
  margin: 0 1rem 1rem 1rem;

  img {
    width: 100%;
    height: 75%;
  }
  div {
    padding-top: 0.5rem;
    height: 25%;
    background-color: $dark-gold;
  }
}
</style>
