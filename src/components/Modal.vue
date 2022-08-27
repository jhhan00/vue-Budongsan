<template>
  <!-- 모달창(팝업창) -->
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <img :src="rooms[pressNum].image" style="width: 90%;">
      <h4> {{ rooms[pressNum].title }} </h4>
      <p> {{ rooms[pressNum].content }} </p>
      <p> {{ rooms[pressNum].price }} 원</p>
      <button @click="modalOpen = false">닫기</button>
    </div>
  </div>
  <!-- 모달창(팝업창) -->
</template>

<script>
export default {
    name : 'ModalPopup',
}
</script>

<style>

</style>