<template>
  <div id="app">
    中午吃什麼？
    <select v-model='selected'>
      <option 
        v-for='(item, index) in locations'
        :value=item.location
        key='index'
      >
        {{item.name}}
      </option>
    </select>
    <button 
      class="vue-btn" 
      title='不可反悔'
      @click='RandomEat'
    >
      點我
    </button>
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
      selected: 'xihu',
      locations: [ 
        {name: '西湖', location: 'xihu'}, 
        {name: '台北車站', location: 'taipei'},
        {name: '迴龍', location: 'huilong'} 
      ],
      eat: '',
      eats: [ 
        {name: '早餐店', price: 40, location: 'xihu'}, 
        {name: '阿婆水餃', price: 70, location: 'xihu'},
        {name: '有禮貌韓式', price: 70, location: 'xihu'},
        {name: '小巷子', price: 100, location: 'xihu'},
        {name: '海霸王炒飯', price: 70, location: 'xihu'},
        {name: '很遠麵線', price: 30, location: 'xihu'},
        {name: '牛肉湯餃', price: 80, location: 'xihu'},
        {name: '麥當勞', price: 100, location: 'xihu'},
        {name: '肯德基', price: 100, location: 'xihu'},
        {name: '香菜甜不辣', price: 40, location: 'xihu'},
        {name: '火車便當', price: 60, location: 'xihu'},
        {name: '吵架花枝羹', price: 60, location: 'xihu'},
        {name: '好吃蛋餅', price: 25, location: 'huilong'},
        {name: '---', price: '---', location: 'taipei'}
      ]
    }
  },
  methods: {
    RandomEat() {
      let location_array = this.eats.filter(this.isValue)
      let previous_eat = this.eat
      let random_id = Math.floor(Math.random() * location_array.length)
      if (location_array[random_id] === previous_eat && location_array.length != 1) {
        this.RandomEat()
      }else {
        this.eat = location_array[random_id]
      }
    },
    isValue(value) {
      return value.location == this.selected
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
