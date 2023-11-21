<template>
  <div class="black-bg" v-if="isModal">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="handleCloseModal">닫기</button>
    </div>
  </div>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  <div v-for="(product, i) in products" :key="product">
    <h4 :style="style" @click="handleOpenModal">{{ product.title }}</h4>
    <img :src="product.image" class="room-img" />
    <p>{{ product.price }}</p>
    <button @click="increase(i)">허위매물 신고</button><br />
    <span>신고수 : {{ 신고수[i] }}</span>
  </div>
</template>

<script>
import oneRoom from "./oneRoom";

export default {
  name: "App",
  data() {
    return {
      products: oneRoom,
      isModal: false,
      style: "color:red",
      menus: ["Home", "Products", "About"],
      신고수: [0, 0, 0, 0, 0, 0],
    };
  },
  methods: {
    increase(index) {
      this.신고수[index] += 1;
    },
    handleOpenModal() {
      this.isModal = true;
    },
    handleCloseModal() {
      this.isModal = false;
    },
  },
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
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
