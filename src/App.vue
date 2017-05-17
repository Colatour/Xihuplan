<template>
  <div id="app">
    {{msg}}
    <br>
    {{eat}}
    <br>
    <button class="vue-btn" @click='GO'>選我</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'Welcome to Xihu',
      eat: '吃什小',
      eats: ['早餐店', '阿婆水餃', '韓式', '小巷子', '海霸王', '麵線']
    }
  },
  methods: {
    GO() {
      let random_id = Math.floor(Math.random() * this.eats.length)
      console.log(random_id)
      this.eat = this.eats[random_id]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
