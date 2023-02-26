<template>
    <div>
    <img :src="원룸들.image" class="room-img">
    <h4>{{원룸들.title}}</h4>
    <p>{{원룸들.price}}원</p>
  </div>
</template>

<script>
export default {
    name : 'Card',
    props: {
      원룸들 : Object,
      누른거 : Number,
    }
    
}
</script>

<style>

</style>