<template>

  <!-- 모달창(팝업창) -->
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <img class="room-img" :src="rooms[pressNum].image">
      <h4> {{ rooms[pressNum].title }} </h4>
      <p> {{ rooms[pressNum].content }} </p>
      <p> {{ rooms[pressNum].price }} 원</p>
      <button @click="modalOpen = false">닫기</button>
    </div>
  </div>
  <!-- 모달창(팝업창) -->

  <div class="menu">
    <a v-for="(menu, idx) in menus" :key="idx">
      {{ menu }}
    </a>
  </div>
  <div v-for="(room, idx) in rooms" :key="idx">
    <img :src="room.image" class="room-img">
    <h4 @click="modalOpen = true; pressNum = idx;"> {{ room.title }} </h4>
    <p> {{ room.price }} 원</p>
  </div>
</template>

<script>

import oneroom from './assets/oneroom.js';

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      menus : ['Home', 'Shop', 'About'],
      notify : [0,0,0],
      modalOpen : false,
      rooms : oneroom,
      pressNum : 0,
    }
  },
  methods : {
    increase(num) {
      this.notify[num] += 1;
    },
  },
}
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 2;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 90%;
  margin-top: 40px;
}

</style>
