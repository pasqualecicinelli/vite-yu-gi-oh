<script>
import PaperList from "./PaperList.vue";

export default {
  data() {
    return {};
  },
  components: { PaperList },
};
</script>

<template>
  <main>

    <div class="container">
      <div class="row flex-wrap">
        <div class="container-col mt-5">
          <div class="col">
            <h5 class="found-card">Found 39 card</h5>
            <PaperList />
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
  height: 100vh;
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
