<template>
  <div>
    <h1>Welcome to Skopos AI</h1>
    <b-tabs v-model="tabIndex" content-class="mt-3">
      <b-tab title="Table">
        <DataTableWrapper :data="tableData()"/>
      </b-tab>
      <b-tab title="Form">
        <EntryForm :weightings="getWeightings()"
                   v-on:submit="onSubmit"  />
      </b-tab>
    </b-tabs>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      portfolio: {},
      tabIndex: 0
    };
  },
  async asyncData({ $axios }) {
    const result = await $axios.get('/portfolio');
    const portfolio = result.data;
    return { portfolio };
  },
  methods: {
    getWeightings() {
      return this.portfolio.weightings.map(weighting =>
      {
        return { 
          ticker: weighting.ticker,
          weight: this.getWeight(this.portfolio)
        };
      });
    },
    tableData() {
      return this.getWeightings();
    },
    async onSubmit(weightings) {
      await this.$axios.post('/portfolio', {
        portfolio: {
          weightings: weightings
        }
      });
      window.location.href = '/';
    },
    getWeight(portfolio) {
      const number = portfolio.weightings.length;
      const percentage = Math.floor(100 / number);
      return percentage;
    },
  }
};
</script>
