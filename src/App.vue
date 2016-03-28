<template>
  <div>
    <div class="condition_box">
      <condition :filter-text.sync="filterText"></condition>
    </div>
    
    <div class="result_box">
      <list :items="filteredItems"></list>
    </div>
  </div>
</template>

<script>
import condition from './components/condition.vue'
import list from './components/list.vue'

export default {
  el: 'body',
  data () {
    return {
      filterText: '',
      items: ['Jack Yang', 'Angel', 'New York']
    }
  },
  components: {
    condition,
    list
  },
  computed: {
    filteredItems: function() {
      return this.$data.items.filter(function(item) {
        return item.indexOf(this.$data.filterText) != -1;
      }.bind(this));
    }
  }
}
</script>

<style scoped>
* {
  margin: 0; 
  padding: 0;
  box-sizing: border-box;
}
.box {
  padding: 10px;
}
</style>
