<!-- Please remove this file from your project -->
<template>
<DataTable
  :header-fields="getHeaderFields()"
  :data="transformedData()"
  :css="datatableCss">
</DataTable>
</template>

<script>
import { DataTable } from 'v-datatable-light';

export default {
  name: "DataTableWrapper",
  components: {
    DataTable
  },
  props: {
    data: {
      type: Object,
      required: true
    }
  },
  methods: {
    transformedData() {
      const rawData = this.data.body;
      return rawData;
    },
    getHeaderFields() {
      return [
        {
          name: 'ticker',
          label: 'Ticker'
        },
        {
          name: 't_date',
          label: 'Date'
        },
        {
          name: 'total_return_index',
          label: 'Total Return Index'
        },
        {
          name: 'price',
          label: 'Price'
        },
        {
          name: 'sector_description',
          label: 'Sector Description'
        },
        {
          name: 'marketcap',
          label: 'Market Cap'
        },
      ]
    }
  },
  data () {
    return {
      datatableCss: {
        table: "table table-bordered table-hover table-striped table-center",
        theadTh: "header-item",
        thWrapper: "th-wrapper",
        thWrapperCheckboxes: "th-wrapper checkboxes",
        arrowsWrapper: "arrows-wrapper",
        arrowUp: "arrow up",
        arrowDown: "arrow down",
        footer: "footer"
      }
    }
  }
};
</script>
