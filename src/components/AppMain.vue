<script>
import PaperList from "./PaperList.vue";
import BaseSelect from "./BaseSelect.vue";
import axios from "axios";

export default {
  data() {
    return {
      apiUriArchetype: "https://db.ygoprodeck.com/api/v7/archetypes.php",
      arrayArchetype: [],
      apiUri: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0",
      arrayCardsPlay: [],
      tipoFiltrato: "",
    };
  },
  components: { PaperList, BaseSelect },

  methods: {
    fetchArchetype(endpoint) {
      axios.get(endpoint).then((response) => {
        this.arrayArchetype = response.data;
      });
    },
    fetchCarte() {
      let url = this.apiUri;

      if (this.tipoFiltrato != "") {
        url += `&archetype=${this.tipoFiltrato}`;
      }
      axios.get(url).then((response) => {
        this.arrayCardsPlay = response.data.data;
      });
    },
    filterType(term) {
      this.tipoFiltrato = term;

      this.fetchCarte();
    },
  },
  created() {
    this.fetchArchetype(this.apiUriArchetype);
    this.fetchCarte();
  },
};
</script>

<template>
  <main>
    <BaseSelect :types="arrayArchetype" @select-type="filterType" />

    <div class="container">
      <div class="row flex-wrap">
        <div class="container-col mt-5">
          <div class="col">
            <h5 class="found-card">Found {{ arrayCardsPlay.length }} cards</h5>

            <PaperList :cardList="arrayCardsPlay" />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
@use "../assets/scss/partials/variables" as *;

main {
  width: 100%;
  height: 100%;
  background-color: $dark-gold;
  padding-top: 5rem;
  position: relative;

  .container {
    max-width: 1200px;
    height: 100%;
    background-color: white;

    .col {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      .found-card {
        width: 96%;
        height: 100px;
        background-color: black;
        color: white;
        line-height: 100px;
        padding-left: 10px;
        margin: 0;
      }
    }
  }
}
</style>
