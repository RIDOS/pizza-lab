<template>
  <div class="container">
    <img src="./assets/logo_200x200.png" alt="pizza">
    <h1>Пиццерия RIDOS!</h1>
    <h3>Кушайте, не обляпайтесь!</h3>
  </div>
  <div>
    <card-container :rewiews="rewiews" :cards="cards"/>
  </div>
</template>

<script>
import CardContainer from '@/components/CardContainer.vue';
import '@fortawesome/fontawesome-free/css/all.css'


export default {
  name: 'App',
  components: {
    CardContainer,
  },

  data() {
    return {
      cards: [
        {
          id: 1,
          title: "Пицца из половинок",
          image: "image-1.webp",
          description: "Выберите пиццы для левой и правой половинки",
          price: 649,
          stock: 10,
          rating: 4,
        },
        {
          id: 2,
          title: "Пицца от шефа",
          image: "image-2.webp",
          description: "Моцарелла, сыры чеддер и пармезан, фирменный соус альфредо",
          price: 289,
          stock: 50,
          rating: 5,
        },
        {
          id: 3,
          title: "Гавайская с альфредо",
          image: "image-3.webp",
          description: "Пастрами из мраморной говядины, сладкий перец, томаты, красный лук",
          price: 419,
          stock: 10,
          rating: 3,
        },
        {
          id: 4,
          title: "Сырная",
          image: "image-4.webp",
          description: "Моцарелла, сыры чеддер и пармезан, фирменный соус альфредо",
          price: 289,
          stock: 0,
          rating: 2,
        },
        {
          id: 5,
          title: "Пицца от шефа",
          image: "image-5.webp",
          description: "Моцарелла, сыры чеддер и пармезан, фирменный соус альфредо",
          price: 289,
          stock: 50,
          rating: 5,
        },
        {
          id: 6,
          title: "Гавайская с альфредо",
          image: "image-6.webp",
          description: "Пастрами из мраморной говядины, сладкий перец, томаты, красный лук",
          price: 419,
          stock: 10,
          rating: 4,
        },
        {
          id: 7,
          title: "Defoult Честер",
          image: "image-7.webp",
          description: "Моцарелла, сыры чеддер и пармезан, фирменный соус альфредо",
          price: 289,
          stock: 50,
          rating: 3,
        },
        {
          id: 8,
          title: "Пицца от черепашек",
          image: "image-8.webp",
          description: "Моцарелла, сыры чеддер и пармезан, фирменный соус альфредо",
          price: 289,
          stock: 0,
          rating: 4,
        },
        {
          id: 9,
          title: "Гавайская с картошкой",
          image: "image-9.webp",
          description: "Пастрами из мраморной говядины, сладкий перец, томаты, красный лук",
          price: 419,
          stock: 10,
          rating: 3,
        },
        {
          id: 10,
          title: "Грибная",
          image: "image-10.webp",
          description: "Моцарелла, сыры чеддер и пармезан, фирменный соус альфредо",
          price: 289,
          stock: 50,
          rating: 5,
        },
      ],
      rewiews: [
        {
          id: 1,
          card_id: 1,
          text: 'Ну норм',
          author: 'Иван Иванович',
          rating: 4,
        },
        {
          id: 2,
          card_id: 1,
          text: 'Хотя... ну нормально',
          author: 'Михаил Миихайлович',
          rating: 3,
        },
        {
          id: 3,
          card_id: 1,
          text: 'Ну да',
          author: 'Артем Арурович',
          rating: 5,
        },
        {
          id: 4,
          card_id: 1,
          text: 'Согласен',
          author: 'Женя Евгеньевич',
          rating: 5,
        },
        {
          id: 5,
          card_id: 5,
          text: 'Хотя... ну нормально',
          author: 'Михаил Миихайлович',
          rating: 3,
        },
        {
          id: 6,
          card_id: 4,
          text: 'Ну да',
          author: 'Артем Арурович',
          rating: 5,
        },
        {
          id: 7,
          card_id: 3,
          text: 'Хотя... ну нормально',
          author: 'Михаил Миихайлович',
          rating: 3,
        },
        {
          id: 8,
          card_id: 2,
          text: 'Ну да',
          author: 'Артем Арурович',
          rating: 5,
        },
        {
          id: 11,
          card_id: 2,
          text: 'Ну не очень :/',
          author: 'Артем Арурович',
          rating: 1,
        },
        {
          id: 9,
          card_id: 7,
          text: 'Хотя... ну нормально',
          author: 'Михаил Миихайлович',
          rating: 3,
        },
        {
          id: 10,
          card_id: 6,
          text: 'Ну да',
          author: 'Артем Арурович',
          rating: 5,
        },
      ],
    };
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h3 {
  font-style: italic;
}
</style>
