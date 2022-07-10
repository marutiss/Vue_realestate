<template>
  <div class="black-bg" v-if="모달창open==true">
  <div class="white-bg">
    <h4>{{원룸들[상품번호].title}}</h4>
      <p>
     <img :src="원룸들[상품번호].image" style="width:100%"><br>
      {{원룸들 [상품번호].content}}<br>
      {{원룸들 [상품번호].price}}원
      </p>
    <!-- <button @click="모달창open=false">닫기</button> -->
  </div>

</div>
</template>

<script>
export default {
    name: 'TheModal',
    props : {
      원룸들 : Array,
      상품번호: Number,
      모달창open: Boolean,
    }

}
</script>

<style>

</style>