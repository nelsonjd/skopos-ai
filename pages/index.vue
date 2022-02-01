<template>
  <div>
    <h1>Welcome to Skopos AI</h1>
    <b-tabs content-class="mt-3">
      <b-tab title="Table" active>
        <DataTableWrapper :data="tableData()"/>
      </b-tab>
      <b-tab title="Form">
        <EntryForm :tickers="getTickers()"  />
      </b-tab>
    </b-tabs>
  </div>
</template>

<script>
import { csv }from 'd3-fetch';

export default {
  name: "IndexPage",
  data() {
    return {
      dataSeries: []
    };
  },
  async fetch() {
    this.dataSeries = [];
  },
  methods: {
    getTickers() {
      return this.tableData().map(datum =>
      {
        return datum.ticker;
      });
    },
    tableData() {
      return [];
    },
  }
};
</script>
