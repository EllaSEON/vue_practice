<template>
  <div class="black-bg" v-if="isModal">
    <div class="white-bg">
      <h4>{{ products[누른거].title }}</h4>
      <img :src="products[누른거].image" style="width: 100%" />
      <p>{{ products[누른거].content }}</p>
      <input v-model="month" />
      <p>
        {{ month }}개월 선택함 :
        {{ (products[누른거].price * month).toLocaleString() }}
      </p>
      <button @click="$emit('handleCloseModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "InfoModal",
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(monthData) {
      if (isNaN(monthData) === true) {
        alert("숫자로 입력하세요");
        this.month = 1;
      }
    },
  },
  props: {
    products: Array,
    누른거: Number,
    isModal: Boolean,
    handleCloseModal: Function,
  },
  emits: ["handleCloseModal"],
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
