<template>
  <div class="total-value" >Balance:
    <span :class='{"color-red": totalBalance < 0, "color-green": totalBalance > 0, "color-black": totalBalance == 0}'>
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
  .color-red{
    color: red
  }
  .color-black{
    color: black
  }
  .color-green{
    color: green
  }
</style>