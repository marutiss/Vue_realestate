<template>

<div class="black-bg" v-if="모달창open==true">
  <div class="white-bg">
    <h4>상세페이지</h4>
    <p>상세내용</p>
    <button @click="모달창open=false">닫기</button>
  </div>

</div>

<div class="menu">
  <a v-for="(a) in 메뉴들" :key="a">{{a}}</a>


</div>




 
  <div v-for="(x,i) in products" :key="i">
    
    <!-- <h4 >{{products[i]}}</h4>
    <p> 50만원</p>
   <button @click="increase">추천!</button> <span>추천수 : {{추천수[i]}}</span> -->
  </div>

 <div v-for="(x,i) in 6" :key="i">
  <img :src="원룸들[i].image" class="room-img">
  <h4 @click="모달창open=true">{{원룸들[i].title}}</h4>
    <p> {{원룸들[i].price}}원</p>
   <button @click="추천수[i]++">추천!</button> <span>추천수 : {{추천수[i]}}</span>
 </div>



</template>

<script>

import room from './assets/roomdata.js';
room;
//import {변수,변수} from './assets/roomdata.js';

export default {
  name: 'App',
  data(){
    return{
      원룸들 : room,
      모달창open : false, 
      추천수:[0,0,0,0,0,0],
     메뉴들: ['Home','Shop','About'],
     products :['역삼동 원룸','천호동 원룸','마포구 원룸'],
    }
  },

  methods:{
    increase(){
    this.추천수++;
    }
  },

components: {
    
  }
}
</script>

<style>
body{
  margin: 0;
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img{
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  margin-top: 60px;
}

.menu{
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px ;
}
.menu a {
  color: white;
  padding: 10px;
}

</style>

<!-- 반복문
// v-for= "(작명,i) in 횟수" :key="작명"
// 횟수 대신 array, object 자료형 가능 >> 자료갯수만큼 반복
// 작명한 변수는 데이터 안의 자료가 된다.
// a는 array자료 i는 1씩증가 
// key 반복돌린 요소를 구분하기 위한 요소

// 데이터 바인딩의 이유 
// {{데이터 바인딩}}
// 1. 하드코딩 해두면 추후 변경 힘듬
// 2. 실시간 렌더링 기능: 데이터를 바꾸면 실시간으로 같이 바꿔줌
// 자주 변할거같은 애들은 바인딩해두자
// HTML 속성은 :속성="데이터 이름" :style="스타일"

UI만들기
0. HTML CSS로 디자인
1.ui의 현상태를 데이터로 저장
2. 데이터에 따라 UI가 어떻게 보일지 작성













-->