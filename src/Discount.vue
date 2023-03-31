<template>
  <div class="discount">
    <h4>지금 결제하면 {{ number }}% 할인</h4>
  </div>
</template>

<script>
export default {
  //eslint-disable-next-line
  name: "Discount",
  data() {
    return {
      number : 20,
    }
  },
  mounted(){
    let timer = setInterval(()=>{
      if(this.number > 0) {
        this.number --;
      }else {
        clearInterval(timer)
      }
    },1000)
  },
  updated(){}
};
</script>

<style>
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
