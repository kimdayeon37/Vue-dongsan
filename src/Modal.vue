<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>{{ onerooms[누른거].title }}</h4>
      <img :src="onerooms[누른거].image" />
      <p>{{ onerooms[누른거].content }}</p>
      <input v-model="month" />
      <p>{{ month }}개월 선택함: {{ onerooms[누른거].price * month }}</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Modal",
  data() {
    return {
      month: 1,
    };
  },

  watch: {
    month(a) {
      if (a > 12) {
        alert("13이상 입력하지 마셈.");
        this.month=1;
      }
      
      // 문자열인지 체크
      if(isNaN(a)==true){
        alert('문자입력금지');
        this.month=1;
      }
      // .... 만 입력하게 될 경우 체크
      if(isNaN(parseFloat(a))) this.month = ''; 
    },
  },
  beforeUpdate(){
    if(this.month == 2){
      alert("3개월이상부터 할부 가능임")
      this.month=3;
    }

  },

  props: {
    onerooms: Array,
    누른거: Number,
    모달창열렸니: Boolean,
  },
};
</script>

<style scoped>
.black-bg {
  width: 100%;
  height: 100%;
  background: (0, 0, 0, 0.5);
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
