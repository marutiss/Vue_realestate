<template>
  <div v-for="(x,i) in 원룸들" :key="i">
    <img :src="원룸들[i].image" class="room-img">
    <!-- <h4 @click="모달창open=true; 상품번호=i">{{원룸들[i].title}}</h4> -->
    <h4 >{{원룸들[i].title}}</h4>
    <p> {{원룸들[i].price}}원</p>
    <!-- <button @click="추천수[i]++">추천!</button> <span>추천수 : {{추천수[i]}}</span> -->
 </div>
</template>

<script>
export default {
    name: 'TheCard',
    props : {
        원룸들: String,
        상품번호: Number,
        
    }
}
</script>

<style>

</style>