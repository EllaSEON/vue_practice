<template>
  <h4 :style="style" @click="handleOpenModal(index)">{{ product.title }}</h4>
  <img :src="product.image" class="room-img" />
  <p>{{ product.price }}</p>
  <button @click="handleIncrease(index)">허위매물 신고</button><br />
  <span>신고수 : {{ 신고수[index] }}</span>
</template>

<script>
export default {
  name: "ProductCard",
  props: {
    product: Object,
    style: String,
    신고수: Array,
    handleOpenModal: Function,
    handleIncrease: Function,
    index: Number,
  },
};
</script>

<style scoped>
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
