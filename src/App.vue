<template>
  <div class="menu">
    <a v-for="(menu, idx) in menus" :key="idx">
      {{ menu }}{{ idx }}
    </a>
  </div>
  <div v-for="(p, idx) in products" :key="idx">
    <h4>{{ p }}</h4>
    <p>{{ price[idx] }} 만원</p>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      products : ['역삼동원룸', '천호동원룸','마포구원룸'],
      menus : ['Home', 'Shop', 'About'],
      price : [50, 60, 80],
    }
  }
}
</script>

<style>
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
</style>
