<script>
export default {
  data() {
    return {
      countInsideArray: 0,
    };
  },

  methods: {},

  props: {
    cardList: Array,
  },

  created() {},
};
</script>

<template>
  <div class="card-img" v-for="(lista, index) in this.cardList" :key="lista.id">
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
