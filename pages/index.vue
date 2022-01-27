<template>
  <div>
    <h1>Welcome to Skopos AI</h1>
    <DataTable />
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  async asyncData({ $content, params }) {
    const data = await $content('price_data_short').limit(500).fetch()
    const result = {
      data: data
    }
    return result;
  }
};
</script>
