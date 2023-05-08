<template>
  <div class="modal-overlay" v-if="visible">
    <div class="modal-window">
      <div class="modal-header">
        <button class="modal-close" @click="closeModal">X</button>
      </div>
      <div v-if="rewiews.find(t => t.card_id == card_id)">
        <div v-for="rewiew in rewiews.filter(t => t.card_id == card_id)" :key="rewiew.id"  class="modal-body" >
            <h3 class="modal-title">Автор: {{ rewiew.author }}</h3>
            <p class="modal-description">Описание: {{ rewiew.text }}</p>
            <div class="modal-rating">
              <i v-for="star in rewiew.rating" :key="star.id" class="fa fa-star" />
            </div>
            <br>
        </div>
      </div>
      <div v-else>
        <h3 class="modal-title">Отзывов на этот товар пока что нет :(</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalContainer",
  props: {
    visible: Boolean,
    rewiews: {
      type: Array,
      default: () => [],
    },
    card_id: Int32Array,
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
  z-index: 9999;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-window {
  background-color: #fff;
  border-radius: 5px;
  padding: 20px;
  width: 40%;
  overflow: auto;
}

.modal-header {
  display: flex;
  justify-content: end;
  align-items: center;
}

.modal-body {
  text-align: left;
}

.modal-header h3 {
  margin: 0;
}

.modal-close {
  border: none;
  background-color: transparent;
  font-size: 24px;
  cursor: pointer;
  outline: none;
}
</style>
