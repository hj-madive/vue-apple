<template>
  <div>
    <Modal :onerooms="onerooms" :modalClick="modalClick" :modalState="modalState" @closeModal="modalState = false" />

    <div class="menu">
      <a v-for="aa in menu" :key="aa">{{ aa }}</a>
    </div>

    <Discount />

    <Card
      @openModal="
        modalState = true;
        modalClick = $event;
      "
      v-for="(oneroom, i) in onerooms"
      :key="i"
      :oneroom="oneroom"
    />
  </div>
</template>

<script>
import data from "./assets/oneroom.js";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      modalClick: 0,
      onerooms: data,
      modalState: false,
      reportCount: [0, 0, 0],
      menu: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increase(i) {
      this.reportCount[i] += 1;
    },
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
  },
};
</script>

<style>
.start {
  opacity: 0;
}
.end {
  opacity: 1;
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.close-btn {
  position: absolute;
  right: 30px;
  top: 30px;
  width: 50px;
  height: 30px;
  border: 0;
  border-radius: 5px;
  background-color: blueviolet;
  color: #fff;
  text-align: center;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
  text-decoration: none;
}
</style>
