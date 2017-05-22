<template>
  <div id="app" class='col-md-8'>
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
    <button class="vue-btn" title='不可反悔' @click='RandomEat'>點我</button>
    <ItemVue :item='eat' />
    <hr>
    <MenuVue :value='eat.value' />
  </div>
</template>

<script>
import ItemVue from './Item.vue'
import MenuVue from './Menu.vue'

export default {
  data () {
    return {
      selected: '---',
      locations: [ 
        {name: '請選擇地區', location: '---'}, 
        {name: '西湖', location: 'xihu'}, 
        {name: '台北車站', location: 'taipei'},
        {name: '迴龍', location: 'huilong'} 
      ],
      eat: '',
      eats: [ 
        {name: '早餐店', value: 'Breakfast', price: 40, location: 'xihu'}, 
        {name: '阿婆水餃', value: 'GrandmotherDumplings' ,price: 70, location: 'xihu'},
        {name: '有禮貌韓式', value: 'CourtesyKoreanRestaurant', price: 70, location: 'xihu'},
        {name: '小巷子', value: 'lane', price: 100, location: 'xihu'},
        {name: '海霸王炒飯', value: 'OnePriceRice', price: 70, location: 'xihu'},
        {name: '很遠麵線', value: 'FarNoodles', price: 30, location: 'xihu'},
        {name: '牛肉湯餃', value: 'BeefSoupDumplings', price: 80, location: 'xihu'},
        {name: '麥當勞', value: 'M', price: 100, location: 'xihu'},
        {name: '肯德基', value: 'KFC', price: 100, location: 'xihu'},
        {name: '香菜甜不辣', value: 'ParsleyBBQ', price: 40, location: 'xihu'},
        {name: '火車便當', value: 'TrainRice', price: 60, location: 'xihu'},
        {name: '吵架花枝羹', value: 'Quarrel', price: 60, location: 'xihu'},
        {name: '好吃蛋餅', value: 'EggCake', price: 25, location: 'huilong'},
        {name: '噴街', value: 'Dirty', price: 100, location: 'taipei'},
        {name: '請選擇地區', value: 'NoSelect', price: '---', location: '---'}
      ]
    }
  },
  components: {
    ItemVue,
    MenuVue
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
  margin-left: 30%;
  margin-right: 30%;
}
</style>
