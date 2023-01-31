<template lang="pug">
.btn-wrap
  button(
    class="btn" 
    :class="{'btn-md' : size === 'medium', 'btn-lg' : size === 'large', 'btn-sm' : size === 'small', 'btn-full' : size === 'full', 'btn-disabled' : disabled }"
    :disabled="disabled"
  ) 
    img(
      v-if="icon" 
        :src="imgSrc" 
        class="mr-2"
      )
    p {{ title }}
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'CmpButton',
  props: {
    title: {
      type: String,
      required: true,
    },
    size: {
      type: String,
      default: 'medium',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    icon: {
      type: String,
      required: false,
    },
  },
  setup(props) {
    const imgSrc = props.icon ? `/src/assets/${props.icon}.svg` : null;

    return {
      imgSrc,
    };
  },
});
</script>

<style lang="scss">
.btn {
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(151.19deg, #4c7ce7 15.36%, #7038e6 96.54%);
  border-radius: 24px;
  outline: none;
  font-weight: bold;
  color: #ffffff;
  border: 0;
  font-size: 20px;
  line-height: 30px;
}

.btn-md {
  width: 200px;
  height: 70px;
}

.btn-lg {
  width: 380px;
  height: 68px;
}

.btn-sm {
  width: 129px;
  height: 50px;
  font-size: 16px;
  line-height: 24px;
}

.btn-disabled {
  background: #eef0f2;
  color: #000000;
}

.btn-full {
  width: 100%;
}
</style>
