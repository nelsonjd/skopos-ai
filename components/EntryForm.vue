<template>
  <div class="container">
    <b-form @submit="onSubmit">
      <b-form-group id="input-group-1" label="Tickers" label-for="input-1">
        <b-form-select
          id="input-1"
          v-model="form.tickers"
          :options="options"
          multiple
          :select-size="4"
        ></b-form-select>
      </b-form-group>
      <b-form-group id="input-group-2" label="Insert a Ticker" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.entry"
          placeholder="Enter ticker symbol"
        ></b-form-input> 
      </b-form-group>
      <b-form-group>
        <b-button v-on:click="onAdd()" variant="secondary">Save Ticker</b-button>
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
        tickers: [],
        entry: ''
      },
      options: this.tickers
    }
  },
  props: {
    tickers: {
      type: Array,
      required: true
    }
  },
  methods: {
    onSubmit (event) { 
      event.preventDefault();
    },
    onAdd() {
      this.tickers.push(this.form.entry);
      this.form.entry = '';
    }
  }
}
</script>