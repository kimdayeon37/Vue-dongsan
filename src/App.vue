<template>
  <transition name="fade">
    <Modal
      @closeModal="모달창열렸니 = false"
      :onerooms="onerooms"
      :누른거="누른거"
      :모달창열렸니="모달창열렸니"
    />
  </transition>

  <div class="menu">
    <a v-for="idx in menu" :key="idx">{{ idx }}</a>
  </div>

  <Discount />

  <button @click="priceSort">가격순정렬</button>
  <button @click="priceUnsort">가격역순정렬</button>
  <button @click="nameSort">가나다순정렬</button>
  <button @click="sortBack">되돌리기</button>

  <Card
    @openModal="
      모달창열렸니 = true;
      누른거 = $event;
    "
    :oneroom="onerooms[i]"
    v-for="(a, i) in onerooms"
    :key="a"
  />
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
      //showDiscount: true,
      oneroomsoriginal: [...data],
      onerooms: data,
      모달창열렸니: false,
      누른거: 0,
      신고수: [0, 0, 0],
      menu: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    priceSort() {
      this.onerooms.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    priceUnsort() {
      this.onerooms.sort(function (a, b) {
        return b.price - a.price;
      });
    },
    nameSort() {
      this.onerooms.sort(function (a, b) {
        return a.title < b.title ? -1 : a.title > b.title ? 1 : 0;
      });
    },
    sortBack() {
      this.onerooms = [...this.oneroomsoriginal];
    },
  },

  // 서버에서 데이터 가져올 때
  created(){
  },

  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
  },
};
</script>

<style>
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  transform: translateY(0);
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  transform: translateY(-1000px);
}

body {
  margin: 0;
}
div {
  box-sizing: border-box;
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
}
</style>
