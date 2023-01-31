<template lang="pug">
.catalog
  CatalogFilters(:amount="40" @openFilters="openFilters").mb-2
  CatalogList(:catalogList="mockGoodsList" :showFilters="showFilters")
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import CatalogFilters from './CatalogFilters.vue';
import CatalogList from './CatalogList.vue';
import mockGoodsList from '../../mocks/goods';

export default defineComponent({
  name: 'CmpCatalog',
  components: { CatalogFilters, CatalogList },
  data() {
    return {
      showFilters: false,
    };
  },
  methods: {
    openFilters(data: boolean) {
      this.showFilters = data;
    },
  },
  setup() {
    const goodsList = mockGoodsList;
    const listLength = ref(goodsList.length);
  },
});
</script>

<style lang="scss" scoped>
.catalog {
  height: 80%;
  overflow: hidden;
}
</style>
