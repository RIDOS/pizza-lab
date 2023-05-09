<template>
  <div @click="showModal" class="card">
    <div class="card-image">
      <img :src="require(`../assets/${card.image}`)" alt="Card Image" />
    </div>
    <div class="card-body">
      <h3 class="card-title">{{ card.title }}</h3>
      <p class="card-description">{{ card.description }}</p>
      <p class="card-description">Размер: {{ card.size }}</p>
      <p class="card-description">Вегетарианская: {{ card.vegan ? 'да' : 'нет' }}</p>
      <div class="card-info">
        <div v-if="card.stock > 0" class="card-price">
          Цена: {{ card.price }} ₽
        </div>
        <div v-if="card.stock === 0" class="card-price">Нет в наличии</div>
        <div class="card-rating">
          <i v-for="star in countStars()" :key="star.id" class="fa fa-star" />
        </div>
      </div>
    </div>
  </div>
  <modal-container
    :visible="isOpen"
    :card_id="card_id"
    :rewiews="rewiews"
    v-if="isOpen"
    @close="hideModal"
  >
  </modal-container>
</template>

<script>
import ModalContainer from "./ModalContainer.vue";

export default {
  components: { ModalContainer },
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Card",
  props: {
    card: {
      type: Object,
    },
    rewiews: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      isOpen: false,
      title: "",
    };
  },
  methods: {
    showModal() {
      this.isOpen = true;
      this.card_id = this.card.id;
      this.title = this.card.title;
    },
    hideModal() {
      this.isOpen = false;
      this.title = "";
      this.card_id = this.card.id;
    },
    countStars() {
      let tmp = this.rewiews.filter((t) => t.card_id === this.card.id);
      let count = 0,
        result = 0;
      let sizeTmp = tmp.length;

      if (tmp.length) {
        for (let i in tmp) {
          count += tmp[i].rating;
        }
        result = Math.floor(count / sizeTmp);
      }
      
      return result;
    },
  },
};
</script>

<style scoped>
.card {
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  margin: 1rem;
  width: 300px;
}

.card-image {
  height: 300px;
  overflow: hidden;
  position: relative;
}

.card-image img {
  object-fit: cover;
  width: 100%;
  height: 100%;
}

.card-body {
  padding: 1rem;
  flex-grow: 1;
}

.card-title {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
}

.card-description {
  margin-bottom: 1rem;
}

.card-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card-price {
  font-size: 1.2rem;
  font-weight: 700;
}
</style>
