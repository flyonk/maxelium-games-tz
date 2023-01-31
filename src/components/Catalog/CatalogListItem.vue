<template lang="pug">
.catalog-item
  .settings(v-if="item.isSettings")
    img(src="../../assets/settings.svg")
  img(
    :src="item.imgSrc" 
    class="catalog-img mb-2"
  )
  .mov-btn(v-if="item.isMove") MOV
  .flex
    img(
      src="../../assets/ragnar.png" 
      with="32" 
      height="32" 
      class="mr-2"
    )
    p.label {{ item.description }}
  p.heading Lorem Impsum Lorem {{ item.id }}
  .controls 
    .controls-inner 
      p.label Price
      p.heading {{ item.price }} SOL
    .controls-inner 
      CmpButton(title="Buy now" size="small")
      img(src="../../assets/heart.svg" width="28")
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import { TCatalogItem } from '../../mocks/goods';
import CmpButton from '../../components/CmpButton.vue';

export default defineComponent({
  name: 'CatalogList',
  components: { CmpButton },
  props: {
    item: {
      type: Object as PropType<TCatalogItem>,
      required: false,
    },
  },
});
</script>

<style lang="scss" scoped>
.catalog-item {
  position: relative;
  padding: 12px;
  display: flex;
  flex-direction: column;
  width: 385px;
  height: 480px;
  background: #ffffff;
  border: 1px solid #c3c6cc;
  border-radius: 20px;
  margin-bottom: 40px;

  &:last-child {
    margin-right: 0;
  }

  > .settings {
    position: absolute;
    top: 8px;
    left: 6px;
  }

  > .mov-btn {
    width: 70px;
    height: 38px;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #ffffff;
    box-shadow: 0px 4px 16px rgba(88, 88, 88, 0.08);
    border-radius: 12px;
    position: absolute;
    right: 20px;
    bottom: 205px;
    font-weight: 600;
    font-size: 14px;
    line-height: 30px;
  }

  > .controls {
    display: flex;
    width: 100%;
    height: 100%;
    align-self: flex-end;

    > .controls-inner {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-self: center;

      &:first-child {
        flex-direction: column;
      }
    }
  }
}

.catalog-img {
  height: 270px;
  width: auto;
  vertical-align: top;
  object-fit: contain;
}
</style>
