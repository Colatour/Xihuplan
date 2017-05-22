<template>
    <div class="col-md-12">
      <div class="character-card">
        <div class="card-block">
          <h4 class="card-title">{{item.name}}</h4>
          <p class="card-text">平均價錢： {{item.price}}</p>
        </div>
      </div>
    </div>
</template>

<script>
    export default {
        props: ['item'],
        data() {
            return {
                _item: ''                
            }
        },
        computed: {
            Get_Item: function() {
                return this._item = this.item
            }
        }
    }
</script>