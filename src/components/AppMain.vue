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
      <div class="row">
        <div class="col">
          <PaperList />
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

  .container {
    max-width: 1200px;
    height: 100%;
    background-color: white;

    .col{
        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
        justify-content: space-between;

    }
  }
}
</style>
