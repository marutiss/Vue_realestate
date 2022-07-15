<template>
  <div >
    <img :src="원룸.image" class="room-img">
    <!-- <h4 @click="모달창open=true; 상품번호=i">{{원룸들[i].title}}</h4> -->
    <h4 @click="함수" >{{원룸.title}}</h4>
    <!-- 클릭하면 부모에게 메세지 전송 -->
<p> {{원룸.price}}원</p>
    
 </div>
</template>

<script>
export default {
    name: 'TheCard',
    props : {
        원룸 : Object,
        상품번호: Number,
        
    },
    methods: {
      함수(){
        this.$emit('openModal', this.원룸.id)
      }
    },
}
</script>

<style>

</style>

