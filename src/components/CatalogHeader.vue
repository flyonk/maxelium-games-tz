<template lang="pug">
.catalog-header 
  img(
    class="logo"
    src="../assets/logo.png"
  )
  CmpInputText(placeholder="Search Web3")
  .flex.nowrap
    p.mr-2.heading Explore
    img(src="../assets/arrowdown.svg")
  CmpButton(title="Connect Wallet")
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import CmpButton from '../components/CmpButton.vue';
import CmpInputText from '../components/CmpInputText.vue';

const searchInput = ref('lol');

export default defineComponent({
  name: 'CatalogHeader',
  components: { CmpButton, CmpInputText },
  props: {
    title: {
      type: String,
      required: false,
    },

    caption: {
      type: String,
      default: '',
    },

    link: {
      type: String,
      default: '#',
    },

    icon: {
      type: String,
      default: '',
    },
  },
});
</script>

<style lang="scss">
.catalog-header {
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-bottom: 50px;

  > .logo {
    width: 270px;
    height: 55px;
  }
}
</style>
