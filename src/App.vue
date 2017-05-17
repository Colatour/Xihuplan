<template>
  <div id="app">
    {{msg}}
    <br>
    {{eat}}
    <br>
    <button class="vue-btn" @click='RandomEat'>選我</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'Welcome to Xihu',
      eat: '吃什小',
      eats: [ 
        '早餐店', 
        '阿婆水餃', 
        '韓式', 
        '小巷子', 
        '海霸王', 
        '很遠麵線', 
        '鬆餅', 
        '湯餃',
        '麥當勞',
        '肯德基',
        '甜不辣',
        '火雞肉飯'
      ]
    }
  },
  methods: {
    RandomEat() {
      let previous_eat = this.eat
      let random_id = Math.floor(Math.random() * this.eats.length)
      if (this.eats[random_id] === previous_eat) {
        this.RandomEat()
      }else {
        this.eat = this.eats[random_id]
      }
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
