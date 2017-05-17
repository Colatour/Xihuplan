<template>
  <div id="app">
    中午要吃什麼？
    <select>
      <option 
        v-for='(item, index) in locations'
        :value=item.value
        key='index'
      >
        {{item.name}}
      </option>
    </select>
    <button class="vue-btn" @click='RandomEat'>選我</button>
    <br>
    <div class="col-md-4">
      <div class="character-card">
        <div class="card-block">
          <h4 class="card-title">{{eat.name}}</h4>
          <p class="card-text">平均價錢： {{eat.price}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      selected: {name: '西湖', value: 'xihu'},
      locations: [ 
        {name: '西湖', value: 'xihu'}, 
        {name: '台北車站', value: 'taipeistation'} 
      ],
      eat: '',
      eats: [ 
        {name: '早餐店', price: 40, location: '西湖'}, 
        {name: '阿婆水餃', price: 70, location: '西湖'},
        {name: '有禮貌韓式', price: 70, location: '西湖'},
        {name: '小巷子', price: 80-100, location: '西湖'},
        {name: '海霸王炒飯', price: 70, location: '西湖'},
        {name: '很遠麵線', price: 30, location: '西湖'},
        {name: '牛肉湯餃', price: 80, location: '西湖'},
        {name: '麥當勞', price: 100, location: '西湖'},
        {name: '肯德基', price: 100, location: '西湖'},
        {name: '香菜甜不辣', price: 40, location: '西湖'},
        {name: '火車便當', price: 60, location: '西湖'},
        {name: '吵架花枝羹', price: 60, location: '西湖'}
      ]
    }
  },
  methods: {
    RandomEat() {
      let array = this.eats.filter(this.isValue)
      let previous_eat = this.eat
      let random_id = Math.floor(Math.random() * this.eats.length)
      if (this.eats[random_id] === previous_eat) {
        this.RandomEat()
      }else {
        this.eat = this.eats[random_id]
      }
    },
    isValue() {
      console.log();
    }
  },
  created() {
    this.RandomEat()
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
