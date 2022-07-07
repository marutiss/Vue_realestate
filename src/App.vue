<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div>
    
    <h4 >{{products[0]}}</h4>
    <p> {{price1}} 50만원</p>
   
  </div>
  <div>
    
    <h4 >{{products[2]}}</h4>
    <p> {{price1}} 60만원</p>
   
  </div>
  <div>
    
    <h4 >{{products[2]}}</h4>
    <p> {{price1}} 70만원</p>
   
  </div>
</template>

<script>


//데이터 바인딩의 이유 
// {{데이터 바인딩}}
// 1. 하드코딩 해두면 추후 변경 힘듬
// 2. 실시간 렌더링 기능: 데이터를 바꾸면 실시간으로 같이 바꿔줌
//자주 변할거같은 애들은 바인딩해두자
//HTML 속성은 :속성="데이터 이름" :style="스타일"



export default {
  name: 'App',
  data(){
    return{
     
     products :['역삼동 원룸','천호동 원룸','마포구 원룸'],
    }
  },

components: {
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
