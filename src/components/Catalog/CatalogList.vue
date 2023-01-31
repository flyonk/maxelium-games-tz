<template lang="pug">
.catalog-wrapper
  CatalogExtendedFilters(v-if="showFilters")
  .catalog-list
    CatalogListItem(v-for="item in goodsList" :key="item.id" :item="item")
    .scroll-wrapper(v-for="(item, id) in endDivs" :key="id")
      .scroll-area(v-scroll-fire="loadGoods")
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import CatalogListItem from './CatalogListItem.vue';
import CatalogExtendedFilters from './CatalogExtendedFilters.vue';
import mockGoodsList from '../../mocks/goods';

const endDivs = ref([0]);
const mockInfiniteScrollCounter = ref(0);
const goodsList = ref(mockGoodsList);

function loadGoods() {
  mockInfiniteScrollCounter.value++;
  if (mockInfiniteScrollCounter.value <= 2) {
    console.log(
      mockInfiniteScrollCounter.value,
      mockInfiniteScrollCounter.value <= 2
    );
    goodsList.value.push(...mockGoodsList);
    endDivs.value.push(Date.now());
  }
}

export default defineComponent({
  name: 'CatalogList',
  components: { CatalogListItem, CatalogExtendedFilters },
  props: {
    catalogList: {
      type: Array,
      required: true,
    },
    showFilters: {
      type: Boolean,
      required: true,
    },
  },
  setup(props) {
    return {
      goodsList,
      loadGoods,
      endDivs,
    };
  },
});
</script>

<style lang="scss" scoped>
.catalog-wrapper {
  display: flex;
  width: 100%;
  height: 100%;
  overflow-y: scroll;
}
.catalog-list {
  padding: 0 10px;
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  justify-content: space-between;
  height: 80%;
  overflow-y: scroll;
}
.scroll-area {
  width: 100%;
  height: 1px;
  margin-bottom: 30px;
}
</style>
