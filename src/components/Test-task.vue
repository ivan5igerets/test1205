<template>
  <div>

    <button class="table-btn" @click="getData" :disabled="isLoading">Get data</button>

    <div v-if="isLoading"> loading.. </div>

    <Table 
      v-if="!isLoading && !isError && tableData.length"
      :tableData="tableData"   
    />

    <div v-if="!isLoading && isError">no data</div>

  </div>
</template>

<script>
import {payload} from '@/mocData'
import simulateAsyncReq from '@/plugins/getDataFunc'
import Table from '@/components/Table'

export default {
  name: 'my-table',
  components: {
    Table
  },
  data() {
    return {
      isLoading: false,
      isError: false,
      tableData: []
    }
  },

  methods: {
    getData() {

      if(this.isLoading) {
        return;
      }

      this.isLoading = true;
      this.tableData = [];

      simulateAsyncReq(payload)
      .then(res => {
        for(let i = 0; i < res.stocks.length; ++i) {
          this.tableData.push({
            stocks: res.stocks[i],
            start: res.start[i],
            current: res.current[i],
          });
        }
        this.sortByStocks();
        this.isLoading = false;
        this.isError = false;
      })
      .catch( () => {
        this.isLoading = false;
        this.isError = true;
      })

    },

    sortByStocks() {
      this.tableData.sort((a, b) => a.stocks > b.stocks ? 1 : -1)
    },
  }
}
</script>