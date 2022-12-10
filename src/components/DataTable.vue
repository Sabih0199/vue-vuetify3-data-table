<template>
  <v-table class="lty-data-table">
    <thead>
      <tr>
        <th v-for="(headItem, headItemIndex) in config" :key="headItemIndex">
          {{ headItem.title.label }}
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(rowDataObj, rowDataIndex) in data" :key="rowDataIndex">
        <td v-for="(cellItem, cellIndex) in config" :key="cellIndex" :class="cellItem.tdClass">
          {{ cellItem?.render && cellItem.render(rowDataObj, rowDataIndex) }}
          <slot :name="cellItem.title.key" :data="rowDataObj"></slot>
        </td>
      </tr>
    </tbody>
  </v-table>
</template>


<script setup lang="ts">
defineProps({
  config: {
    type: Array,
    required: false,
    default: null
  },
  data: {
    type: Array,
    required: false,
    default: null
  }
});
</script>