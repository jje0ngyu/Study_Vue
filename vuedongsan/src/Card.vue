<template>
    <div>
    <img :src="원룸들.image" class="room-img">
    <h4 @click="함수">{{원룸들.title}}</h4>
    <p>{{원룸들.price}}원</p>
  </div>
  <!-- custom event
   이걸로 부모데이터 수정해야 된다. (실은 데이터 수정해달라는 메시지이고, 실제로 데이터를 수정하지는 않는다.)
    $emit('작명', 데이터)
    $ 표시는 뷰에 내장된 것
    자식이 보낸 데이터는 부모 컴포넌트에서 $event 변수를 사용하면 담긴 내용을 확인할 수 있다.
  -->
</template>

<script>
export default {
    name : 'Card',
    props: {
        // props로 보낸 데이터는 수정금지 (Read-only)
        // 부모의 데이터를 수정 (custom event)
        원룸들 : Object,
    },
    // $emit()을 함수 안에서 사용하고 싶으면
    // + props든, data든, $변수든 밑에서 쓸 땐 this 붙여야 한다.
    methods : {
        함수(){
            this.$emit('openModal', this.원룸들.id)
        }
    }
    
}
</script>

<style>

</style>