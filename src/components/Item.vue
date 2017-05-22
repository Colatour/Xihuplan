<template>
    <div class="col-md-4">
      <div class="character-card">
        <div class="card-block">
          <h4 class="card-title">{{Get_Item_computed.name}}</h4>
          <p class="card-text">平均價錢： {{Get_Item_computed.price}}</p>
        </div>
      </div>
      <hr>
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
            Get_Item_computed: function() {
                return this._item = this.item
            }
        }
    }
</script>