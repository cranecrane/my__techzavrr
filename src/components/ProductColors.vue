<template>
  <ul class="colors" :class="bgLight ? 'colors--black' : {}">
    <li class="colors__item" v-for="color in colors" :key="color.id">
      <label class="colors__label" :for="`${listData.id}-${color.id}`">
        <input class="colors__radio sr-only" type="radio" :id="`${listData.id}-${color.id}`" :value="color.id" v-model="currentColorId"/>
        <span class="colors__value" :style="{ 'background-color': color.hex }"></span>
      </label>
    </li>
  </ul>
</template>

<script>
import colorsLib from '@/data/colors';

export default {
  props: ['listData', 'bgLight', 'activeColor'],
  computed: {
    currentColorId: {
      get() {
        return this.activeColor;
      },
      set(value) {
        this.$emit('update:activeColor', value);
      },
    },
    colors() {
      return colorsLib.filter((color) => this.listData.colors.includes(color.id));
    },
  },
};
</script>
