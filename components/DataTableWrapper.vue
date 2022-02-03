<!-- Please remove this file from your project -->
<template>
  <div class="container">
    <DataTable
      :header-fields="getHeaderFields()"
      :data="data"
      :css="datatableCss"
    >
    </DataTable>
  </div>
</template>

<script>
import { DataTable } from "v-datatable-light";

export default {
  name: "DataTableWrapper",
  components: {
    DataTable,
  },
  props: {
    data: {
      type: Array,
      required: true,
    },
  },
  methods: {
    transformedData() {
      const rawData = this.data.body;
      return rawData;
    },
    getHeaderFields() {
      return [
        {
          name: "ticker",
          label: "Ticker",
        },
        {
          name: "weight",
          label: "Weighting"
        }
      ];
    },
  },
  data() {
    return {
      datatableCss: {
        table: "table table-bordered table-hover table-striped table-center",
        theadTh: "header-item",
        thWrapper: "th-wrapper",
        thWrapperCheckboxes: "th-wrapper checkboxes",
        arrowsWrapper: "arrows-wrapper",
        arrowUp: "arrow up",
        arrowDown: "arrow down",
        footer: "footer",
      },
    };
  },
};
</script>
