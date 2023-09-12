<script>
import axios from "axios";

export default {
  data() {
    return {
      arrayList: [],
      countInsideArray: 0,
    };
  },

  methods: {
    fetchCarte() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
        .then((response) => {
          this.arrayList = response.data.data;
          console.log(this.arrayList);
        });
    },
  },

  created() {
    this.fetchCarte();
  },
};
</script>

<template>
  <div card-img v-for="(lista, index) in arrayList" :key="lista.id">
    <img :src="lista.card_images[countInsideArray].image_url" alt="" />
    <p>{{ lista.name }}</p>
    <p>{{ lista.archetype }}</p>
  </div>
</template>

<style lang="scss" scoped>

  
    
    img {
    width: 50%;
    height: 80%;
  }

</style>
