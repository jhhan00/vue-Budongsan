<template>
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="modalOpen = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, idx) in menus" :key="idx">
      {{ menu }}
    </a>
  </div>
  <div v-for="(room, idx) in rooms" :key="idx">
    <img :src="room.image" class="room-img">
    <h4> {{ room.title }} </h4>
    <p> {{ room.price }} 원</p>
  </div>
  <!-- <div>
    <img :src="rooms[0].image" class="room-img">
    <h4> {{ rooms[0].title }} </h4>
    <p> {{ rooms[0].price }} 원 </p>
  </div>
  <div>
    <img src="./assets/room1.jpg" class="room-img">
    <h4> {{ products[1] }} </h4>
    <p>70 만원</p>
  </div>
  <div>
    <img src="./assets/room2.jpg" class="room-img">
    <h4> {{ products[2] }} </h4>
    <p>50 만원</p>
  </div> -->
</template>

<script>

import oneroom from './assets/oneroom.js';

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      products : ['역삼동원룸', '천호동원룸','마포구원룸'],
      menus : ['Home', 'Shop', 'About'],
      notify : [0,0,0],
      modalOpen : false,
      rooms : oneroom,
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
