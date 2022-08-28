<template>
  <!-- 모달창(팝업창) -->
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <img :src="rooms[pressNum].image" style="width: 90%;">
      <h4> {{ rooms[pressNum].title }} </h4>
      <p> {{ rooms[pressNum].content }} </p>
      <input v-model.number="month" />
      <p> {{month}} 개월 선택함 : {{ rooms[pressNum].price * month}} 원</p>
      <button @click="modalCloseFunc">닫기</button>
    </div>
  </div>
  <!-- 모달창(팝업창) -->
</template>

<script>
export default {
    name : 'ModalPopup',
    props : {
        // props로 받아온 데이터들은 read-only == 값 변경 X
        rooms : Array,
        pressNum : Number,
        modalOpen : Boolean,
    },
    data() {
        return {
            month : 1,
        }
    },
    methods : {
        modalCloseFunc() {
            this.$emit('closeModal');
        }
    },
}
</script>

<style>

</style>