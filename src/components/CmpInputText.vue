<template lang="pug">
input(
  class="text-input"
  type="text" 
  :placeholder="placeholder"
)
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'CmpButton',
  props: {
    placeholder: {
      type: String,
      default: 'medium',
    },
  },
});
</script>

<style lang="scss">
.text-input {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 19px 18px;
  gap: 10px;
  width: 536px;
  height: 68px;
  background: #f1f2f4;
  border-radius: 24px;
}
</style>
