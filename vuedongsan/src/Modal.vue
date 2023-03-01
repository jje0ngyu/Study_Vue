<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <!-- if문 연달아 쓰고 싶을 때 : v-if="" / v-else-if="" / v-else -->
    <div class="white-bg">
      <h4>{{ 원룸들[누른거].title }}</h4>
      <img :src="원룸들[누른거].image" style="width:100%">
      <p>{{원룸들[누른거].content}}</p>
      <!-- <input @input="month = $event.target.value"> -->
      <input v-model.number="month">
      <!-- v-model="데이터이름"을 사용하면 input류에 입력한 데이터를 "데이터이름"에 바로 값을 넣어준다.
        <textarea> 에서도 v-model을 사용할 수 있다. 단,
            문자로 입력받기 때문에 data()에서 초깃값을 스트링 타입으로 해줘야한다.
            ex) month = '',
        <select> 에서도 v-model을 사용할 수 있다.
            <option>의 값을 "데이터이름"에 저장된다.
        <input type="checkbox" v-model="데이터이름">
            checkbox의 값은 true/false로 표시
      -->
      <!--
        @input : 입력할 때마다 실행하기
        @change : 입력 후 다른 곳을 마우스클릭 했을 때 실행하기
      -->
      <p>{{month}}개월 선택함 : {{원룸들[누른거].price * month}}원</p>
      <button @click="함수">닫기</button>
      <!-- props는 read-only 이므로, 받아온 거 수정하면 큰일남
       잘못된 예시 : <button @click="모달창열렸니 = false">닫기</button>
      -->
    </div>
  </div>
</template>

<script>
export default {
    name : 'Modal',
    data(){
        return {
            month : 1, // 초기값
        }
    },

    // 데이터를 감시하려면? watch!
    watch : {
        // 함수 식으로 관리
        // 데이터명으로...
        // "month"라는 데이터가 변할 때마다 실행
        month(a){
            // 파라미터는 2개까지 작성 가능하며 ex) month(a,b)
            // a,b = month 데이터  (*a: 변경 후 / b: 변경 전)
            // 일반적으로 변경 후 데이터가 중요하므로 a를 기준으로 watch 실행
            // 사용자가 month에 입력한 데이터가 13보다 크면 경고문 띄우기
            if (isNaN(a) == true){
                alert('문자는 입력하지 마세요');
                this.month = 1;                
            }
        }
        // 유효성 검사를 직접 치기 귀찮다면, Vue전용 라이브러리
        // form validation 을 설치 !!
        // 그럼 watcher 안 써도 됨
    },
    props: {
        // 자식은 props로 받은 거 등록
        // props : {데이터이름 : 자료형이름}
        원룸들 : Array, // 받아온 데이터의 자료형 이름을 대문자로
        누른거 : Number,
        모달창열렸니 : Boolean,
    },
    methods: {
        함수(){
            this.$emit('closeModal')
        }
    }
}
</script>

<style>

</style>