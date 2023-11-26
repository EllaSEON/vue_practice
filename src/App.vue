<template>
  <info-modal
    :products="products"
    :누른거="누른거"
    :isModal="isModal"
    :handle-close-modal="handleCloseModal"
  />
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  <shop-discount />
  <product-card
    v-for="(product, i) in products"
    :key="product.id"
    :index="i"
    :product="product"
    :신고수="신고수"
    :handleIncrease="handleIncrease"
    :handleOpenModal="handleOpenModal"
    :style="style"
  />
</template>

<script>
import oneRoom from "./assets/oneRoom";
import ShopDiscount from "./components/ShopDiscount.vue";
import InfoModal from "./components/InfoModal.vue";
import ProductCard from "./components/ProductCard.vue";

export default {
  name: "App",
  data() {
    return {
      누른거: 0, // 사용자가 누른 상품번호 0번째 상품 누르면 0, 1번째 상품 누르면 1
      products: oneRoom,
      isModal: false,
      style: "color:red",
      menus: ["Home", "Products", "About"],
      신고수: [0, 0, 0, 0, 0, 0],
    };
  },
  methods: {
    handleIncrease(index) {
      this.신고수[index] += 1;
    },
    handleOpenModal(index) {
      this.isModal = true;
      this.누른거 = index;
    },
    handleCloseModal() {
      this.isModal = false;
    },
  },
  components: { ShopDiscount, InfoModal, ProductCard },
};
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
body {
  margin: 0;
}
div {
  box-sizing: border-box;
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
