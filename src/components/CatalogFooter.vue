<template lang="pug">
.catalog-footer 
  .footer-inner
    p © QUANTELICA, 2022. All right reserved
  .footer-inner
    p Privacy Policy
    p Terms of Service
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'CatalogFooter',
  components: {},
  props: {
    title: {
      type: String,
      required: false,
    },
  },
});
</script>

<style lang="scss">
.catalog-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 100px;
  border-top: 0.6px solid #b5bcc9;
}

.footer-inner {
  display: flex;

  > p {
    margin-left: 20px;
    font-weight: 600;
    font-size: 20px;
    line-height: 24px;
    color: #b5bcc9;
  }
}
</style>
