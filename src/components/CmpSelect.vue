<template lang="pug">
.select-input 
  p.mr-2 {{ title }}
  img(src="../assets/arrowdown.svg")
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'CmpSelect',
  props: {
    title: {
      type: String,
      required: true,
    },
  },
});
</script>

<style lang="scss">
.select-input {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 16px 28px;
  gap: 12px;
  width: 136px;
  height: 62px;
  font-weight: 600;
  font-size: 16px;
  line-height: 22px;
  text-align: center;
  color: #0b0b0c;
  background: #f1f2f4;
  border-radius: 20px;
}
</style>
