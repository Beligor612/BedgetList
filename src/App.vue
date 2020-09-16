<template>
  <div id="app">
    <BudgetList :list="list" @deleteItem = "onDelete"/>
    <TotalBalance :totalBalance="totalBalance"/>
    <Form @submitForm="submitForm"/>
  </div>
</template>

<script>
import BudgetList from './components/BudgetList';
import TotalBalance from './components/TotalBalance';
import Form from './components/Form'

export default {
  name: 'App',
  components: {
    BudgetList,
    TotalBalance,
    Form
  },
  data: () => ({
    list: {
      1: {
        type: 'INCOME',
        value: 100,
        comment: 'Some comments',
        id: 1,
      },
      2: {
        type: 'OUTCOME',
        value: -50,
        comment: 'Some comments2',
        id: 2,
      }
    }
  }),
  computed: {
    totalBalance(){
      return Object.values(this.list).reduce((acc, item) => acc += item.value, 0)
    }
  },
  methods: {
    onDelete: function(id){
      this.$delete(this.list, id)
    },
    submitForm(formData){
      const newObj = {
        ...formData,
        id: String(Math.random())
      }
      this.$set(this.list, newObj.id, newObj)
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
  margin-top: 60px;
}
</style>
