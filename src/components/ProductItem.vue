<template>
  <li class="catalog__item">
    <a class="catalog__pic" href="#" @click.prevent="gotoPage('product', {id: product.id})">
      <img :src="product.image" :alt="product.title" />
    </a>

    <h3 class="catalog__title">
      <a href="#">
        {{ product.title }}
      </a>
    </h3>

    <span class="catalog__price">
      {{ product.price | numberFormat }} ₽
    </span>

    <ProductColors :list-data="product" :bg-light="true" :activeColor.sync="currentColor"/>
  </li>
</template>

<script>
import ProductColors from '@/components/ProductColors.vue';
import gotoPage from '@/helpers/gotoPage';
import numberFormat from '@/helpers/numberFormat';

export default {
  data() {
    return {
      currentColor: 0,
    };
  },
  props: ['product'],
  components: { ProductColors },
  filters: {
    numberFormat,
  },
  methods: {
    gotoPage,
  },
};
</script>
