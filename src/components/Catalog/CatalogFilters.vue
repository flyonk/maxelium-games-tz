<template lang="pug">
.catalog-filters
  .catalog-filters--inner
    CmpButton(
      title="FILTERS" 
      size="large" 
      icon="filters" 
      class="mr-2" 
      @click="openFilters"
    )
    CmpInputText(
      placeholder="Search Web3" 
      class="w-full"
    )
  .catalog-filters--inner
    .items {{ itemsOnSale }} Items on sale
    .controllers
      CmpSelect(title="Status" class="mr-2")
      CmpSelect(title="Type" class="mr-2")
      CmpSelect(title="Game" class="mr-2")
      CmpSelect(title="Collection" class="mr-2")
      CmpSelect(title="Recently Listed" class="mr-2")

</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import CmpButton from '../../components/CmpButton.vue';
import CmpInputText from '../../components/CmpInputText.vue';
import CmpSelect from '../../components/CmpSelect.vue';

export default defineComponent({
  name: 'CatalogFilters',
  components: { CmpButton, CmpInputText, CmpSelect },
  props: {
    amount: {
      type: Number,
      required: false,
    },
  },
  data() {
    return {
      isShowFilter: ref(false),
    };
  },
  methods: {
    openFilters() {
      this.isShowFilter = !this.isShowFilter;
      this.$emit('openFilters', this.isShowFilter);
    },
  },
  setup(props) {
    const itemsOnSale = ref(props.amount);
    return {
      itemsOnSale,
    };
  },
});
</script>

<style lang="scss" scoped>
.catalog-filters {
  display: flex;
  flex-direction: column;
  margin-bottom: 30px;

  &--inner {
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: flex-end;
    flex-wrap: nowrap;

    &:first-child {
      margin-bottom: 30px;
    }

    > .items {
      font-weight: 600;
      font-size: 20px;
      line-height: 30px;
      text-align: center;
      color: #b5bcc9;
      white-space: nowrap;
    }

    > .controllers {
      display: flex;
    }
  }
}
</style>
