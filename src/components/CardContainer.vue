<template>
  <div class="card-container">
    <Card v-for="(card, index) in cards" :key="index" :card="card" :rewiews="rewiews" />
  </div>
</template>

<script>
import Card from "./Card.vue";

export default {
  name: "CardContainer",
  components: {
    Card,
  },
  props: {
    cards: {
      type: Array,
      default: () => [],
    },
    rewiews: {
      type: Array,
      default: () => [],
    }
  },
};
</script>

<style scoped>
.card-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
