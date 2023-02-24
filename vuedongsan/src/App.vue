<template>
  <!-- 모달창 -->
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <!-- 반복적인 <a>가 등장할 때 반복문을 사용하고 싶지 않나요?
      HTML 반복문 : <태그 v-for="작성 in 반복횟수"> (:key="작명"도 필요) 
      Vue반복문 특징 : array / object 집어넣기 가능
      - 1. 자료 안에 데이터 갯수만큼 반복
      - 2. 작명한 변수는 데이터 안의 자료가 됨
      - 3-1. 변수 작명 2개까지 가능
      - 3-2. <a v-for="(a,i) in 메뉴들" :key="i"> {{ a }} </a>
      - 3-3. 왼쪽변수 : array 내의 데이터
      - 3-4. 오른쪽변수 : 1씩 증가하는 정수 
    -->
    <a v-for="작명 in 메뉴들" :key="작명">{{ 작명 }}</a>

  </div>
  <!-- 반복문 추가 예시
    <div v-for="점포명 in products" :key="점포명">
      <h4 class="red" :style="스타일">{{ products }}</h4>
      <p>50만원</p>
    </div>
  -->
  <!-- 또는 
    <div v-for="(점포명,i) in 3" :key="i">
      <h4 class="red" :style="스타일">{{ products[i] }}</h4>
      <p>50만원</p>
    </div>
  -->




  <!--  
    오늘 배울 내용
    이벤트 핸들러 : HTML 클릭 시 코드실행하는 법

    ↓↓↓ 기존 자바스크립트 클릭 이벤트
     <button onClick="">
    ↓↓↓ 뷰의 이벤트
     <button v-on:click="">
     <button @click="">  => 'v-on'의 약자가 '@'이다.
    
    다양한 이벤트 사용가능
     @click
     @mouseover
     @input : 글자를 입력했을 때 자바스크립트 실행

    Q. 입력할 코드가 좀 길면...
    A. 함수명을 사용
    ↓↓↓ 기존 자바스크립트 함수
     function 어쩌구() {}
    ↓↓↓ 뷰의 함수 
    methods : { 함수(){ 내용어쩌구저쩌구 } }
  -->
  



  <div>
    <img src="./assets/room0.jpg" class="room-img">
    <!-- ./  부터가 현재 위치 -->
    <h4 @click="모달창열렸니 = true">{{ products[0] }}</h4>
    <p>50만원</p>
    <button @click="신고수[0]++">허위매물신고</button>
    <span>신고수 : {{신고수[0]}}</span>
  </div>
  <div>
    <img src="./assets/room1.jpg" class="room-img">
    <h4>{{ products[1] }}</h4>
    <p>50만원</p>
    <button @click="신고수[1]++">허위매물신고</button>
    <span>신고수 : {{신고수[1]}}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" class="room-img">
    <h4>{{ products[2] }}</h4>
    <p>50만원</p>
    <button @click="신고수[2]++">허위매물신고</button>
    <span>신고수 : {{신고수[2]}}</span>
  </div>
</template>

<script>
// ★★★ 실시간 미리보기
// Terminal > New Terminal > npm run serve 입력



// * 문법만 외우면 개발자가 아니다. 혼자서 코드를 못 짜기 때문이다
// * 이 문법을 언제 쓰는지 배워야한다

// ###### 데이터바인딩 ######
// - JS데이터를 HTML에 꽂아넣는 문법
// ↓↓↓ 기존 자바스크립트식 데이터바인딩
// document.getElementById().innerHTML = ??
// ↓↓↓ 뷰의 데이터바인딩
// data() { return { '이곳에 데이터 넣기 '}}

// 데이터바인딩하는 이유1
//   HTML에 하드코딩해놓으면 나중에 변경이 어렵다.
//   가변적인 데이터는 밑에 작성한다.
// 데이터바인딩하는 이유2
//    Vue의 실시간 자동 렌더링 쓰려면 해야한다.
//    data를 변경하면 data와 관련된 HTML에도 실시간으로 반영된다.
//    웹앱 같은거 만들 수 있다.

// => 자주 변할 것 같은 데이터들은 데이터로 보관하고 HTML에 {{꽂아넣자}}
//    스무스하게 페이지 데이터가 가변하므로 너무 좋다!

// Q. 쇼핑몰 이름도 데이터바인딩 할까?
// A. No. 애초에 바뀔 일이 없으면 안 해도 된다.


// (충격) HTML 속성도 데이터바인딩 가능 !!
// 속성 값을 데이터바인딩 할 때에는 콧수염{{}}이 아니라
// 콜론(:)을 붙여준다! ex) :style="스타일"


// 동적인 UI 만드는 법 :
// 1. UI의 현재 상태를 데이터로 저장
// 2. 데이터에 따라 UI가 어떻게 보일지 작성


import apple from './assets/oneroom.js';
apple;

export default {
  name: 'App',
  data(){
    return{
      // object형식으로 자료 저장 → {자료이름 : 자료내용}
      price1 : 60,
      // 한글로 작명 가능
      스타일 : 'color : blue',
      모달창열렸니 : false, // 1 or 0 , true or false
      신고수 : [0, 0, 0],
      메뉴들 : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods : {
     increase(){
      // Vue에서 함수 만들 때 주의사항
      // - 함수 안에서 데이터 쓸 땐 this.데이터명
      this.신고수 += 1;
     }
  },
  components: {
  }
}
</script>

<style>
body {
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width : 100%; height : 100%;
  background : rgba(0,0,0,0.5);
  position : fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
.room-img {
  width : 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

</style>
