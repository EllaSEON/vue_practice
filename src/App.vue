<template>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  <div v-for="(product, i) in products" :key="product">
    <h4 :style="style">{{ product }}</h4>
    <p>50 만원</p>
    <button @click="increase(i)">허위매물 신고</button><br />
    <span>신고수 : {{ 신고수[i] }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      style: "color:red",
      menus: ["Home", "Products", "About"],
      신고수: [0, 0, 0],
    };
  },
  methods: {
    increase(index) {
      this.신고수[index] += 1;
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
