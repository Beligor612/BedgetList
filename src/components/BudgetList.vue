<template>
  <div class="budget-list-wrap">
    <el-card :header="header">
      <template v-if="isEmpty" >
        <div class="list-item" v-for="(item, prop) in list" :key="prop">
          <BudgetListItem :item="item" @deleteItem="deleteItem"/>
        </div>
      </template>
      <template v-else>
        <el-alert
          type="info" title="No budget">
        </el-alert>
      </template>
    </el-card>
  </div>
</template>


<script>
import BudgetListItem from './BudgetListItem'

export default {
  components: {
    BudgetListItem,
  },
  name: "BudgetList",
  data: ()=> ({
    header: 'Budget List'
  }),
  props:{
    list: {
      type: Object,
      default: () => {}
    }
  },
  computed:{
    isEmpty(){
      return Object.keys(this.list).length
    }
  },
  methods: {
    deleteItem: function(id){
      this.$emit('deleteItem', id)
    }
  }
}
</script>

<style scoped>
.budget-list-wrap{
    max-width: 500px;
    margin: auto;
  }
</style>