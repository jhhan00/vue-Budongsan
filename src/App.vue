<template>
  <!-- <div class="start" :class="{ end : modalOpen }">
    <Modal 
      :rooms="rooms" 
      :pressNum="pressNum" 
      :modalOpen="modalOpen"
      @closeModal="modalOpen = false">
    </Modal>
  </div> -->

  <transition name="fade">
    <Modal 
      :rooms="rooms" 
      :pressNum="pressNum" 
      :modalOpen="modalOpen"
      @closeModal="modalOpen = false">
    </Modal>
  </transition>

  <div class="menu">
    <a v-for="(menu, idx) in menus" :key="idx">
      {{ menu }}
    </a>
  </div>

  <Discount
    v-if="showDiscount"
    :discountNum="discountNum"/>

  <button @click="initSort">되돌리기</button>
  <button @click="priceAscSort">가격 정렬</button>
  <button @click="priceDescSort">가격 역정렬</button>
  <button @click="productNameSort">상품명 정렬</button>

  <Card 
    v-for="(room, idx) in rooms"
    :key="idx"
    :room="room"
    @openModal="modalOpen = true; pressNum = $event">
  </Card>

</template>

<script>
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';
import Card from './components/Card.vue';

import oneroom from './assets/oneroom.js';

export default {
  name: 'App',
  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  },
  data() {
    return {
      menus : ['Home', 'Shop', 'About'],
      notify : [0,0,0],
      modalOpen : false,
      rooms : oneroom,
      originRooms : [...oneroom],
      pressNum : 0,
      discountNum : 10,
      showDiscount : true,
    }
  },
  methods : {
    increase(num) {
      this.notify[num] += 1;
    },
    initSort() {
      this.rooms = [...this.originRooms];
    },
    priceAscSort() {
      this.rooms.sort(function(r1,r2) {
        return r1.price - r2.price;
      });
    },
    priceDescSort() {
      this.rooms.sort(function(r1, r2) {
        return r2.price - r1.price;
      });
    },
    productNameSort() {
      this.rooms.sort(function(r1, r2) {
        var x = r1.title.toLowerCase();
        var y = r2.title.toLowerCase();

        if(x > y) return 1;
        else if(x < y) return -1;
        return 0;
      });
    },
  },
  mounted() {
    setInterval(() => {
      if(this.discountNum > 0) this.discountNum -= 1;
    }, 1000);
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

.start {
  opacity: 0;
  transition: all 1s;
}

.end {
  opacity: 1;
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

/**
  transition 태그에서 모달창이 열릴 때 실행되는 css
 */
.fade-enter-from {
  /* 시작 시 */
  /* opacity: 0; */
  transform: translateY(-1000px);
}
.fade-enter-active {
  /* 애니메이션 효과 진행 */
  transition: all 1s;
}
.fade-enter-to {
  /* 끝날 시 */
  /* opacity: 1; */
  transform: translateY(0px);
}

/**
  transition 태그에서 모달창이 닫힐 때 실행되는 css
 */
.fade-leave-from {
  /* 시작 시 */
  opacity: 1;
}
.fade-leave-active {
  /* 애니메이션 효과 진행 */
  transition: all 1s;
}
.fade-leave-to {
  /* 끝날 시 */
  opacity: 0;
}

</style>
