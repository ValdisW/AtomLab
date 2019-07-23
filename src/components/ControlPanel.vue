<template>
  <v-container fluid grid-list-lg>
    <v-layout row wrap>
      <v-flex shrink style="width: 60px">
        <v-text-field v-model="price[0]" class="mt-0" hide-details single-line type="number"></v-text-field>
      </v-flex>

      <v-flex>
        <v-range-slider v-model="price" :max="600" :min="20" :step="10"></v-range-slider>
      </v-flex>

      <v-flex shrink style="width: 60px">
        <v-text-field v-model="price[1]" class="mt-0" hide-details single-line type="number"></v-text-field>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      price: [110, 440]
    };
  }
};
</script>

<style scoped>
</style>
