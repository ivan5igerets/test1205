<template>
    <div class="table">
          
      <div class="table-header">
        <div class="table-header-item left">Stocs</div>
        <div class="table-header-item">Current</div>
        <div class="table-header-item right">Change</div>
      </div>

      <div class="table-row" v-for="(item, i) in tableData" :key="i">
        <div class="table-row-item left"> {{item.stocks}} </div>
        <div class="table-row-item"> {{item.current.toFixed(2) }} </div>
        <div class="table-row-item right" :class="{red: (item.current - item.start) < 0,green: (item.current - item.start) >= 0 }" > {{ (item.current - item.start).toFixed(2) }} </div>
      </div>
    
    </div>
</template>

<script>
export default {
    props: ['tableData']
}
</script>

<style lang="scss">
.table {
  width: 400px;
  margin: 0 auto;
  border: 1px solid #c5c5c5;
  border-radius: 3px;
  overflow: hidden;

  &-btn {
    background: #ececec;
    padding: 5px 30px;
    font-size: larger;
    border-radius: 3px;
    border: 1px solid #c5c5c5;
    margin-top: 50px;
    margin-bottom: 20px;
  }

  &-header {
    background: #ececec;
    display: flex;
        
    &-item {
      margin: 15px;
      font-weight: 700;
      flex: 1; 
    }
  }

  &-row {
    display: flex;
    border-top: 1px solid #c5c5c5;

    &-item {
      margin: 15px;
      flex: 1;
    }
  }
}

.left {
  text-align: left;
}

.right {
  text-align: right;
}

.red {
  color: red;
}

.green {
  color: green;
}
</style>