<template>



  <!-- <div class="start" :class="{end : 모달창open}"> -->
  <!--clss조건부 
    {클래스명 : 조건}-->
  
  <transition name="fade">
  <Modal @closeModal="모달창open=false" :원룸들="원룸들" :상품번호="상품번호" :모달창open="모달창open"/>
  </transition>
  
  <!-- </div> -->



  <div class="menu">
    <a v-for="(a) in 메뉴들" :key="a">{{a}}</a>
  </div>


  <discount v-if="showdiscount==true" @closediscount="showdiscount=false" />


  <button @click="Hpricesort">높은가격순정렬</button>
  <button @click="Lpricesort">낮은가격순정렬</button>
  <button @click="sortLang">이름순정렬</button>
  <button @click="sortback">복구</button>

  <div v-for="(x,i) in products" :key="i">
    
    <!-- <h4 >{{products[i]}}</h4>
    <p> 50만원</p>
   <button @click="increase">추천!</button> <span>추천수 : {{추천수[i]}}</span> -->
  </div>

  
  
  <!-- 만약 card 컴포넌트에서 반복문 안쓰면 -->
  <!-- <Card :원룸="원룸들[0]"/>
  <Card :원룸="원룸들[1]"/>
  <Card :원룸="원룸들[2]"/>
  <Card :원룸="원룸들[3]"/>
  <Card :원룸="원룸들[4]"/>
  <Card :원룸="원룸들[5]"/>  -->
  <!-- 축약하면-->
  <Card @openModal="모달창open=true; 상품번호=$event"  :원룸="원룸들[i]" v-for="(작명,i) in 원룸들" :key="작명" />
  <!--@'자식컴포넌트가 보낸거'로 메세지 수신  -->
</template>

<script>
import room from './assets/roomdata.js';
import BannerDiscount from './components/BannerDiscount.vue';
import TheModal from './components/TheModal.vue';
import TheCard from './components/TheCard.vue';



//import {변수,변수} from './assets/roomdata.js';

export default {
  name: 'App',
  data(){
    return{
      showdiscount: true,
      원룸원본: [...room],
      오브젝트 :{name:'kim', age:20},
      상품번호: 0,
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
    },
    Hpricesort(){
      this.원룸들.sort(function(a,b){
        return b.price-a.price  //JS실력임
      })
    },
    Lpricesort(){
      this.원룸들.sort(function(a,b){
        return a.price-b.price  //JS실력임
      })
    },
    
    //문자 배열
    sortLang(){
      this.원룸들.sort(function(a,b){
        return a.title.localeCompare(b.title)
      })
    },  
    sortback(){
      this.원룸들=[...this.원룸원본];
    },
  },

  // mounted(){
  //   setTimeout(() => {
  //     this.showdiscount=false;
  // }, 2000);
  // }, 
  //app.vue가 mount되고나서 실행


components: {
  
    discount : BannerDiscount, //왼쪽이름으로 오른쪽 사용하겠음
    Modal : TheModal,
    Card : TheCard,
  }
}
</script>

<style>
.fade-enter-from{
  opacity: 0;
}
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  opacity: 1;
}
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

동적 UI만들기
0. HTML CSS로 디자인
1.ui의 현상태를 데이터로 저장
2. 데이터에 따라 HTML/UI가 어떻게 보일지 작성
3. @click등으로 UI조작할 방법 만들기

컴포넌트 왜씀??
재사용하기 쉽게됨 , 공간정리가 어썸함
나중에 수정하기 정말 편함
>>반복할 부분만 컴포넌트

컴포넌트 쓰는법
1. vue파일 import
2. component{} 등록
3.사용
>>컴포넌트.vue 이름은 2단어 이상 사용해야한다.
  싫다면
  package.json 파일열기 >> rules항목
  >>"vue/multi-word-component-names":"off"
  >>아니면 여러단어를 쓰자

부모/자식 컴포넌트
app: 부모 ,modal: 자식
부모랑 자식 둘다 쓰는 데이터면 부모에 기록할것
자식은 부모의 데이터를 props로 받아서 쓴다.
props는 읽기 전용이다.
1. 임포트
2. 등록
3. 사용 
4. 자식컴포넌트에게 props로 데이터 주기

<props자료 작명="문자자료">
<props자료 :작명="숫자자료">
<props자료 :작명="Array,object">

custom event
1. 자식이 부모에게 요청하기 
>> $emit('작명',데이터)

CSS로 에니메이션 만들기
1. 시작전에 class명 부여
2. 끝난후 clss명 생성
3. 원할때 2번 부착
근데 vue눈 transition 쓰면됨
1. 애니할곳에 transition 부착
2. 클래스명 3개 스타일에 작성
  .작명-enter-from{} 시작 스타일
  .작명-enter-active{}
  .작명-enter-to{} 끝 스타일

  .작명-leave-from{} 시작 스타일
  .작명-leave-active{}
  .작명-leave-to{} 끝 스타일

정렬시키기
만약 원룸들 정렬시
  바닐라js면 원룸들 데이터 정렬>>HTML에 반영
  vue는 데이터 정렬 끝

sort()>> 배열안에 숫자가 있다면 오름차순으로 왼쪽부터 배열
      >>원본이 아예 변형됨

원본데이터 보호를 위해서는??
사본을 만들고 사본을 사용하자>>원룸들 : room, 원룸원본: [...room],
[...데이터] 해서 사본을 만들자

lifeCycle의 매인은 hook이다. 이거 쓸려고 배우는거야
ajax는 created, mounted안에 적어서 요청





-->