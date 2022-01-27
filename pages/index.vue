<template>
  <div>
    <h1>Welcome to Skopos AI</h1>
    <DataTableWrapper :data="data"/>
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
