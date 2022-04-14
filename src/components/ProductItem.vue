<template>
  <li class="catalog__item">
    <a class="catalog__pic" href="#">
    <img :src="product.image" :alt="product.title">
    </a>

    <h3 class="catalog__title">
    <a href="#">
        {{ product.title }}
    </a>
    </h3>

    <span class="catalog__price">
      {{ product.price }}
    </span>

    <ul class="colors colors--black">
      <li class="colors__item" v-for="color in colors" :key="color.id">
        <label class="colors__label" :for="`${product.id}-${color.id}`">
        <input class="colors__radio sr-only" type="radio" :id="`${product.id}-${color.id}`"
        :value="color.id" v-model="activeColor">
        <span class="colors__value" :style="{ 'background-color': color.hex }">
        </span>
        </label>
      </li>
  </ul>
  </li>
</template>

<script>
import colorsLib from '../data/colors';

export default {
  data() {
    return {
      activeColor: 0,
    };
  },
  props: ['product'],
  computed: {
    colors() {
      return colorsLib.filter((color) => this.product.colors.includes(color.id));
    },
  },
};
</script>
