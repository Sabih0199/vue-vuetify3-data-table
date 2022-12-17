<script setup lang="ts">
import { reactive, computed } from "vue"

const props = defineProps({
  config: {
    type: Array<{
      tdClass?: string,
      title: { label: string, key: string },
      render?: (data: any) => { data },
      sortable?: boolean
    }>,
    required: true,
    default: null
  },
  data: {
    type: Array,
    required: true,
    default: null
  },
  tableClass: {
    type: String,
    required: false,
    default: null
  },
  searchClass: {
    type: String,
    required: false,
    default: null
  },
  paginationClass: {
    type: String,
    required: false,
    default: null
  },
});

const states = reactive({
  currentSort: "",
  currentSortDir: 'asc',
  pageSize: 10,
  currentPage: 1,
  searchString: ""
});

const sortKeys = Object.keys(props.data[0]);

const sortColumn = (key: string) => {
  states.currentSort = key;
  if (key === states.currentSort) {
    states.currentSortDir = states.currentSortDir === 'asc' ? 'desc' : 'asc';
  }
};

const sortedData = computed(() => {
  return states.searchString === ""
    ?
    props.data.sort((a: any, b: any) => {
      let modifier = 1;
      if (states.currentSortDir === 'desc') modifier = -1;
      if (a[states.currentSort] < b[states.currentSort]) return -1 * modifier;
      if (a[states.currentSort] > b[states.currentSort]) return 1 * modifier;
      return 0;
    }).filter((row, index) => {
      let start = (states.currentPage - 1) * states.pageSize;
      let end = states.currentPage * states.pageSize;
      if (index >= start && index < end) return true;
    })
    : props.data.filter(item => Object.values(item).join("").toString().toLowerCase().indexOf(states.searchString.toString().toLowerCase()) !== -1);
})

const nextPage = () => {
  if ((states.currentPage * states.pageSize) < props.data.length) states.currentPage++;
};

const prevPage = () => {
  if (states.currentPage > 1) states.currentPage--;
};
</script>

<template>
  <v-text-field v-model="states.searchString" placeholder="search" type="search" class="vv3-data-table-search"
    :class="props.searchClass" hide-details />
  <v-table class="vv3-data-table" :class="props.tableClass">
    <thead>
      <tr>
        <th v-for="(headItem, headItemIndex) in config" :key="headItemIndex">
          {{ headItem?.title?.label }} <v-icon @click="sortColumn(sortKeys[headItemIndex])"
            v-if='headItem?.sortable'>mdi-sort-alphabetical-{{ states.currentSortDir }}ending</v-icon>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(rowDataObj, rowDataIndex) in sortedData" :key="rowDataIndex">
        <td v-for="(cellItem, cellIndex) in config" :key="cellIndex" :class="cellItem?.tdClass">
          {{ cellItem?.render && cellItem.render(rowDataObj) }}
          <slot :name="cellItem?.title?.key" :data="rowDataObj"></slot>
        </td>
      </tr>
    </tbody>
  </v-table>
  <v-pagination class="vv3-data-table-pagination" :class="props.paginationClass" v-model="states.currentPage"
    :length="props.data.length / states.pageSize" :on-prev="prevPage" :on-next="nextPage" />
</template>