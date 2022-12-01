<template>
</template>

<script>
module.exports = {
  created() {

    window.myNamespace = {

      highPriceCellClass: function (params) {
        return params.value > 32000 ? 'price-high' : '';
      },

      highPriceWithConfigCellClass: function (maxPrice) {
        return function (params) {
          return params.value > maxPrice ? 'price-high' : '';
        };
      },

      highPriceTooltipComponent: class {
        init(params) {
          const eGui = this.eGui = document.createElement('div');

          if (params.value > 32000) {
            eGui.classList.add('my-tooltip');
            eGui.innerHTML = 'value to high';
          }
        }

        getGui() {
          return this.eGui;
        }
      },
    }
  },
}
</script>

<style id="myNamespace">
.ag-cell-not-inline-editing.price-high {
  background-color: red;
  color: white;
}

.my-tooltip {
  background-color: white;
  border: 1px solid black;
  padding: 8px;
}
</style>
