<template>
  <div class="total-value" >Balance:
    <span class="value">
      {{ totalBalance }}
    </span>
    </div>
</template>

<script>
export default {
  name: "TotalBalance",
  data: ()=> ({

  }),
  props: {
    totalBalance: {
      type: Number,
      default: 0,
    }
  }
}
</script>

<style scoped>
  .total-value{
    margin: 15px 0px;
    font-weight: bold;
  }
  .value{
    color: red
  }
</style>