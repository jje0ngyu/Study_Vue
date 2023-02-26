<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <!-- if문 연달아 쓰고 싶을 때 : v-if="" / v-else-if="" / v-else -->
    <div class="white-bg">
      <h4>{{ 원룸들[누른거].title }}</h4>
      <img :src="원룸들[누른거].image" style="width:100%">
      <p>{{원룸들[누른거].content}}</p>
      <p>{{원룸들[누른거].price}}</p>
      <!-- <button @click="모달창열렸니 = false">닫기</button> -->
      <!-- props는 read-only 이므로, 받아온 거 수정하면 큰일남
       잘못된 예시 : <button @click="모달창열렸니 = false">닫기</button>
      -->
    </div>
  </div>
</template>

<script>
export default {
    name : 'Modal',
    props: {
        // 자식은 props로 받은 거 등록
        // props : {데이터이름 : 자료형이름}
        원룸들 : Array, // 받아온 데이터의 자료형 이름을 대문자로
        누른거 : Number,
        모달창열렸니 : Boolean,
    }
}
</script>

<style>

</style>