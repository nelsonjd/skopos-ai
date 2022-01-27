<template>
  <div>
    <h1>Welcome to Skopos AI</h1>
    <b-tabs content-class="mt-3">
      <b-tab title="Table" active>
        <DataTableWrapper :data="data"/>
      </b-tab>
      <b-tab title="Form">
        <EntryForm />
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

  }
};
</script>
