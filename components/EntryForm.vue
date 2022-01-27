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
      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        tickers: []
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
    }
  }
}
</script>