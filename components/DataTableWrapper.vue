<!-- Please remove this file from your project -->
<template>
<DataTable
  :header-fields="headerFields"
  :data="data">
</DataTable>
</template>

<script>
import { DataTable } from 'v-datatable-light';

export default {
  name: "DataTableWrapper",
  components: {
    DataTable
  },
  data: function() {
    return {
      data: [
        {
          ticker: 'GOOG',
          price: 12.3
        },
        {
          ticker: 'AAPL',
          price: 30.3
        }
      ],
      headerFields: [
        {
          name: 'ticker',
          label: 'Ticker',
        },
        {
          name: 'price',
          label: 'Price'
        }
      ]
    }
  }
};
</script>
