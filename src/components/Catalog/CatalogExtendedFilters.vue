<template lang="pug">
.extended-filters
  .filters-inner
    h4 Filter by
    p Clear all
  h6 price
  .filters-inner
    input(type="text" class="mini-input" placeholder="min")
    p.hyphen -
    input(type="text" class="mini-input" placeholder="max")
    CmpButton(
      class="mt-2"
      title="Apply" 
      size="medium" 
      disabled 
    )
  h6 rarity
  .filters-inner
    .checkbox-wrapper(ref="eyes")
      .flex.justify-between.w-full.mb-2
        h6 Eyes
        img(src="../../assets/arrowup.svg" @click="closeMenu('eyes')")
      ul.list.eyes-list
        li(
          v-for="(item, index) in eyesList" 
          :key="index" 
          class="item"
        )
          input(type="checkbox" class="checkbox-input")
          p.name {{ `${item.color} ${item.amount}` }}
    .checkbox-wrapper(ref="hair")
      .flex.justify-between.w-full.mb-2
        h6 Hair
        img(src="../../assets/arrowup.svg" @click="closeMenu('hair')")
      ul.list.eyes-list
        li(
          v-for="(item, index) in hairStyleList" 
          :key="index" 
          class="item"
        )
          input(type="checkbox" class="checkbox-input")
          p.name {{ `${item.color} ${item.amount}` }}
    .checkbox-wrapper(ref="ears")
      .flex.justify-between.w-full.mb-2
        h6 Ears
        img(src="../../assets/arrowup.svg" @click="closeMenu('ears')")
      ul.list.eyes-list
        li(
          v-for="(item, index) in earsList" 
          :key="index" 
          class="item"
        )
          input(type="checkbox" class="checkbox-input")
          p.name {{ `${item.style} ${item.amount}` }}
  h6 game properties
  .filters-inner
    .checkbox-wrapper(ref="transport")
      .flex.justify-between.w-full.mb-2
        h6 Transport
        img(src="../../assets/arrowup.svg" @click="closeMenu('transport')")
      ul.list.eyes-list
        li(
          v-for="(item, index) in transportList" 
          :key="index" 
          class="item"
        )
          input(type="checkbox" class="checkbox-input")
          p.name {{ `${item.name} ${item.amount}` }}
    .checkbox-wrapper(ref="magic")
      .flex.justify-between.w-full.mb-2
        h6 Magic items
        img(src="../../assets/arrowup.svg" @click="closeMenu('magic')")
      ul.list.eyes-list
        li(
          v-for="(item, index) in magickList" 
          :key="index" 
          class="item"
        )
          input(type="checkbox" class="checkbox-input")
          p.name {{ `${item.name} ${item.amount}` }}
    .checkbox-wrapper(ref="weapon")
      .flex.justify-between.w-full.mb-2
        h6 Weapon
        img(src="../../assets/arrowup.svg" @click="closeMenu('weapon')")
      ul.list.eyes-list
        li(
          v-for="(item, index) in weaponList" 
          :key="index" 
          class="item"
        )
          input(type="checkbox" class="checkbox-input")
          p.name {{ `${item.name} ${item.amount}` }}
    .range-wrapper(ref="power")
      .flex.justify-between.w-full.mb-2
        h6.mb-1 Power
        img(src="../../assets/arrowup.svg" @click="closeMenu('power')")
      .flex.justify-between
        input(type="text" class="mini-input" placeholder="min")
        p.hyphen -
        input(type="text" class="mini-input" placeholder="max")
      input(type="range" class="input-range mt-2")
    .range-wrapper(ref="speed")
      .flex.justify-between.w-full.mb-2
        h6.mb-1 Speed
        img(src="../../assets/arrowup.svg" @click="closeMenu('speed')")
      .flex.justify-between
        input(type="text" class="mini-input" placeholder="min")
        p.hyphen -
        input(type="text" class="mini-input" placeholder="max")
      input(type="range" class="input-range mt-2")
    .range-wrapper(ref="defence")
      .flex.justify-between.w-full.mb-2
        h6.mb-1 Defence
        img(src="../../assets/arrowup.svg" @click="closeMenu('defence')")
      .flex.justify-between
        input(type="text" class="mini-input" placeholder="min")
        p.hyphen -
        input(type="text" class="mini-input" placeholder="max")
      input(type="range" class="input-range mt-2")

</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import CmpButton from '../../components/CmpButton.vue';
import CatalogListItem from './CatalogListItem.vue';

export default defineComponent({
  name: 'CatalogList',
  components: { CatalogListItem, CmpButton },
  props: {
    catalogList: {
      type: Array,
      required: true,
    },
  },
  methods: {
    closeMenu(type: string) {
      const closestTarget = this.$refs[type];
      if (closestTarget.classList.contains('opened')) {
        closestTarget.classList.remove('opened');
      } else {
        closestTarget.classList.add('opened');
      }
    },
  },
  setup() {
    const eyesList = ref([
      {
        color: 'Blue',
        amount: '45',
      },
      {
        color: 'Red',
        amount: '25',
      },
      {
        color: 'Green',
        amount: '115',
      },
      {
        color: 'Yellow',
        amount: '6',
      },
    ]);

    const hairStyleList = ref([
      {
        color: 'Kare',
        amount: '7',
      },
      {
        color: 'Long',
        amount: '225',
      },
      {
        color: 'Short-hair',
        amount: '5',
      },
      {
        color: 'Something',
        amount: '11',
      },
    ]);

    const earsList = ref([
      {
        style: 'Pink',
        amount: '600',
      },
      {
        style: 'Cutted',
        amount: '1',
      },
      {
        style: 'Mike Tyson Style',
        amount: '555',
      },
      {
        style: 'Elf style',
        amount: '123',
      },
    ]);

    const transportList = ref([
      {
        name: 'Car',
        amount: '100',
      },
      {
        name: 'Cadillac',
        amount: '64',
      },
      {
        name: 'Airplane',
        amount: '31',
      },
      {
        name: 'Jet-ski',
        amount: '10',
      },
    ]);

    const magickList = ref([
      {
        name: 'Fireball',
        amount: '151',
      },
      {
        name: 'Ice Nova',
        amount: '222',
      },
      {
        name: 'Stormblast',
        amount: '1',
      },
      {
        name: 'Summon Golem',
        amount: '51',
      },
    ]);

    const weaponList = ref([
      {
        name: 'Sword',
        amount: '5',
      },
      {
        name: 'Arballet',
        amount: '22',
      },
      {
        name: 'Axe',
        amount: '11',
      },
      {
        name: 'Knife',
        amount: '709',
      },
    ]);

    return {
      eyesList,
      hairStyleList,
      earsList,
      transportList,
      magickList,
      weaponList,
    };
  },
});
</script>

<style lang="scss">
.extended-filters {
  width: 380px;
  border: 1px solid #e4e5e7;
  border-radius: 16px;
  padding: 22px;
  margin-right: 40px;

  > .filters-inner {
    display: flex;
    width: 100%;
    justify-content: space-between;
    margin-bottom: 45px;
    flex-wrap: wrap;

    > h4 {
      font-weight: 700;
      font-size: 20px;
      line-height: 30px;
      text-transform: uppercase;
      color: #0b0b0c;
    }

    > p {
      font-weight: 600;
      font-size: 20px;
      line-height: 30px;
      color: #969aa0;
    }

    > .checkbox-wrapper {
      max-height: 56px;
      overflow: hidden;
      width: 100%;
      background: #f7f7f9;
      border-radius: 12px;
      padding: 12px;
      margin-bottom: 12px;

      > .list {
        display: flex;
        flex-direction: column;

        > .item {
          display: flex;
          margin-bottom: 5px;

          > .checkbox-input {
            margin-right: 10px;
          }
        }
      }
    }

    > .checkbox-wrapper.opened {
      max-height: 300px;
    }
  }

  > h6 {
    font-weight: 700;
    font-size: 24px;
    line-height: 30px;
    text-transform: uppercase;
    color: #0b0b0c;
    margin-bottom: 15px;
  }
}

.range-wrapper {
  width: 100%;
  max-height: 56px;
  padding: 12px;
  background: #f7f7f9;
  border-radius: 12px;
  overflow: hidden;
  margin-bottom: 12px;
}

.range-wrapper.opened {
  max-height: 148px;
}

.mini-input {
  padding: 16px 18px;
  width: 104px;
  height: 54px;
  background: #f7f7f9;
  border-radius: 12px;
}

.hyphen {
  align-self: center;
}

.input-range {
  width: 100%;
}
</style>
