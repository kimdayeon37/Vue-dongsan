<template>
  <div class="discount">
    <h4>지금 사면 {{ amount }}% 할인!</h4>
  </div>
</template>

<script>
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Discount',
    data(){
      return {
        amount: 30,
      }
    },

     mounted() {
      const intervalId = setInterval(()=>{
      this.amount--;
    },1000);
    setTimeout(function(){
    clearInterval(intervalId);
}, 30000);
  },
}
</script>

<style scoped>
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
