<template>
  <div class="container">
    <b-form @submit="onSubmit">
      <b-form-group
        id="input-group-2"
        label="Insert a Ticker"
        label-for="input-2"
      >
        <b-form-input
          id="input-2"
          v-model="form.entry"
          v-on:input="clear"
          placeholder="Enter ticker symbol"
        ></b-form-input>
        <span class="error-message" v-if="form.errorPresent">Invalid Entry</span>
      </b-form-group>
      <b-form-group>
        <b-button v-on:click="onAdd()" variant="secondary">Add Ticker</b-button>
      </b-form-group>

      <h4>Portfolio Selections</h4>
      <b-container>
        <b-row>
          <b-col>
            <b>Ticker</b>
          </b-col>
          <div class="col-sm">
            <b>Weighting</b>
          </div>
        </b-row>
        <b-row v-for="stock in form.portfolio" :key="stock" class="row">
          <b-col>
            {{ stock }}
          </b-col>
          <b-col>{{ getWeighting() }}%</b-col>
        </b-row>
      </b-container>
      <b-form-row class="py-5">
        <b-button type="submit" variant="primary">Submit</b-button>
      </b-form-row>
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
        errorPresent: false
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
      if (!this.valid(this.form.entry)) {
        this.form.errorPresent = true;
        return;
      }
      this.form.portfolio.push(this.form.entry);
      this.form.entry = "";
    },
    getWeighting() {
      const number = this.form.portfolio.length;
      const percentage = Math.floor(100 / number);
      return percentage;
    },
    valid(entry) {
      const failsWhitespace = /\s+/.test(entry);
      const upperEntry = entry.toUpperCase()
      return upperEntry === entry && !failsWhitespace;
    },
    clear(event) {
      this.form.errorPresent = false;
    }
  },
};
</script>

<style scoped>
.error-message {
  color: red;
}
</style>