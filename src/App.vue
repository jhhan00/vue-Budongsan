<template>

  <Modal 
    :rooms="rooms" 
    :pressNum="pressNum" 
    :modalOpen="modalOpen">
  </Modal>

  <div class="menu">
    <a v-for="(menu, idx) in menus" :key="idx">
      {{ menu }}
    </a>
  </div>

  <Discount/>

  <div v-for="(room, idx) in rooms" :key="idx">
    <img :src="room.image" class="room-img">
    <h4 @click="modalOpen = true; pressNum = idx;"> {{ room.title }} </h4>
    <p> {{ room.price }} 원</p>
  </div>
</template>

<script>
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';

import oneroom from './assets/oneroom.js';

export default {
  name: 'App',
  components: {
    Discount : Discount,
    Modal : Modal,
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
  padding: 15px;
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
  /* border-radius: 5px; */
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 90%;
  margin-top: 20px;
}

</style>
