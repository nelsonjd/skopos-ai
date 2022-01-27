<template>
  <div class="container">
    <b-form @submit="onSubmit">
      <b-form-group id="input-group-1" label="Tickers" label-for="input-1">
        <b-form-select
          id="input-1"
          v-model="form.portfolio"
          :options="options"
          multiple
          :select-size="4"
        ></b-form-select>
      </b-form-group>
      <b-form-group
        id="input-group-2"
        label="Insert a Ticker"
        label-for="input-2"
      >
        <b-form-input
          id="input-2"
          v-model="form.entry"
          placeholder="Enter ticker symbol"
        ></b-form-input>
      </b-form-group>
      <b-form-group>
        <b-button v-on:click="onAdd()" variant="secondary"
          >Add Ticker</b-button
        >
      </b-form-group>
      <b-form-group>
        <div class="container">
          <h4>Portfolio Selections</h4>
          <div class="row">
            <div class="col-sm">
              <b>Ticker</b>
            </div>
            <div class="col-sm">
              <b>Weighting</b>
            </div>
          </div>
          <div v-for="stock in form.portfolio" :key="stock" class="row">
            <div class="col-sm">
              {{ stock }}
            </div>
            <div class="col-sm">
              {{ getWeighting() }}%
            </div>
          </div>
        </div>
      </b-form-group>
      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        portfolio: [],
        entry: "",
      },
      options: this.tickers,
    };
  },
  props: {
    tickers: {
      type: Array,
      required: true,
    },
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
    },
    onAdd() {
      this.tickers.push(this.form.entry);
      this.form.entry = "";
    },
    getWeighting() {
      const number = this.form.portfolio.length;
      const percentage = Math.floor(100 / number);
      return percentage;
    }
  },
};
</script>