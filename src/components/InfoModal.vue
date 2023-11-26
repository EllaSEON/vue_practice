<template>
  <div class="black-bg" v-if="isModal">
    <div class="white-bg">
      <h4>{{ products[누른거].title }}</h4>
      <img :src="products[누른거].image" style="width: 100%" />
      <p>{{ products[누른거].content }}</p>
      <p>{{ products[누른거].price.toLocaleString() }}</p>
      <button @click="handleCloseModal">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "InfoModal",
  props: {
    products: Array,
    누른거: Number,
    isModal: Boolean,
    handleCloseModal: Function,
  },
};
</script>

<style>
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
</style>
