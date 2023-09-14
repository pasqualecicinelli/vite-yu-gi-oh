<script>
export default {
  data() {
    return {
      searchType: "",
    };
  },
  props: {
    types: Array,
  },

  emits: ["select-type"],
};
</script>

<template>
  <div class="container">
    <select
      v-model="searchType"
      @change="$emit('select-type', searchType)"
      class="form-select"
      aria-label="Default select example"
    >
      <option
        v-for="(type, index) in types"
        :key="index"
        :value="type.archetype_name"
      >
        {{ type.archetype_name }}
      </option>
    </select>
  </div>
</template>

<style lang="scss" scoped>
@use "../../src/assets/scss/partials/variables" as *;

.container {
  select {
    width: 200px;
  }
}
</style>
