<template>
  <select v-model="sortBy" style="">
    <option value="price-asc">Цена (по возрастанию)</option>
    <option value="price-desc">Цена (по убыванию)</option>
    <option value="size-asc">Размер (по возрастанию)</option>
    <option value="size-desc">Размер (по убыванию)</option>
    <option value="rewie-asc">Репутация (по возрастанию)</option>
    <option value="rewie-desc">Репутация (по убыванию)</option>
    <option value="vegan">Вегетарианска :/</option>
  </select>
  <div class="card-container">
    <Card
      v-for="(card, index) in sortedCards"
      :key="index"
      :card="card"
      :rewiews="rewiews"
    />
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
    },
  },
  data() {
    return {
      sortBy: "price-asc",
    };
  },
  computed: {
    sortedCards() {
      let sortedCards = [...this.cards];
      if (this.sortBy === "price-asc") {
        sortedCards.sort((a, b) => a.price - b.price);
      } else if (this.sortBy === "price-desc") {
        sortedCards.sort((a, b) => b.price - a.price);
      } else if (this.sortBy === "size-asc") {
        sortedCards.sort((a, b) => a.size - b.size);
      } else if (this.sortBy === "size-desc") {
        sortedCards.sort((a, b) => b.size - a.size);
      } else if (this.sortBy === "rewie-asc") {
        let sortedRewiews = [...this.rewiews].sort((a, b) => b.rating - a.rating);
        sortedCards.filter(a => a.id === sortedRewiews.card_id);
      } else if (this.sortBy === "rewie-desc") {
        let sortedRewiews = [...this.rewiews].sort((a, b) => b.rating - a.rating);
        sortedCards.filter(a =>  a.id === sortedRewiews.card_id);
      } else if (this.sortBy === "vegan") {
        alert("Больной ублюдок! >:(");
        sortedCards.sort((a, b) => b.vegan - a.vegan);
      }
      return sortedCards;
    },
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
