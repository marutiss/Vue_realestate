<template>
  <div class="black-bg" v-if="모달창open==true">
  <div class="white-bg">
    <h4>{{원룸들[상품번호].title}}</h4>
      <p>
     <img :src="원룸들[상품번호].image" style="width:100%"><br>
      {{원룸들 [상품번호].content}}<br></p>
      <input v-model.number="month">
      <!-- <input @input="month=$event.target.value"> -->
      <!--"$event.target.value" 사용자가 입력한 값 쌩js문법-->
      <p>{{month}}개월 선택함: {{원룸들 [상품번호].price*month}}원</p>
   <button @click="$emit('closeModal')">닫기</button>
  </div>

</div>
</template>

<script>
export default {
    name: 'TheModal',
    data(){
      return{
        month: 1,
      }
    },
    props : {

      원룸들 : Array,
      상품번호: Number,
      모달창open: Boolean,
    }

}
</script>

<style>

</style>

<!--
input으로 입력한 값을 데이터로 저장
1. <input @input="month=$event.target.value">
  "$event.target.value" 사용자가 입력한 값 쌩js문법
  month를 data안에 넣어주면 됨
2. <input v-model="month">
 해당기능은 textarea나 select에도 사용가능
만약 month의 초기값을 문자로 하면 문자를 입력받고
숫자를 입력하면 숫자를 입력받는다>>근데 문자 자료형으로 저장됨 >>근데 연산은됨

덧셈하면 '문자'+숫자
.number 하면 숫자데이터로 저장



-->