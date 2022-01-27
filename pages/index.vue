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
export default {
  name: "IndexPage",
  async asyncData({ $content, params }) {
    const data = await $content('price_data_short').fetch();
    
    return { data };
  },
  methods: {
    getTickers() {
      return this.tableData().map(datum =>
      {
        return datum.ticker;
      });
    },
    tableData() {
      return this.data.body;
    },
  }
};
</script>
