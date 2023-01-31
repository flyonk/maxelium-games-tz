<template lang="pug">
CatalogHeader
CmpCatalog
CatalogFooter
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CatalogHeader from '../components/CatalogHeader.vue';
import CatalogFooter from '../components/CatalogFooter.vue';
import CmpCatalog from '../components/Catalog/CmpCatalog.vue';

export default defineComponent({
  name: 'IndexPage',
  components: { CatalogHeader, CmpCatalog, CatalogFooter },
});
</script>
