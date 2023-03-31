<template>
  <div class="black-bg" v-if="modalState == true">
    <div class="white-bg">
      <h4>{{ onerooms[modalClick].title }}</h4>
      <img class="room-img" :src="onerooms[modalClick].image" alt="" />
      <p>
        {{ onerooms[modalClick].content }}
      </p>
      <!-- <input @input="month = $event.target.value" /> -->
      <input v-model="month" />
      <p>{{ month }} 개월 선택함 : {{ onerooms[modalClick].price * month }} 원</p>
      <button @click="$emit('closeModal')" class="close-btn">닫기</button>
    </div>
  </div>
</template>
<script>
export default {
  //eslint-disable-next-line
  name: "Modal",
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(a) {
      console.log(a);
      if (isNaN(a) === true) {
        alert("숫자만 쓰시오");
        this.month = 1  ;
      }
    },
  },
  beforeUpdate() {
    if(this.month == 2) {
      alert('2 쓰지마시오');
      this.month = 3
    }
  },
  props: {
    onerooms: Array,
    modalClick: Number,
    modalState: Boolean,
  },
};
</script>
<style></style>
