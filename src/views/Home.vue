<template>
  <div class="page">
    <h2>Home</h2>
    <div class="product-list">
      <ProductCard v-for="item of catalog" v-bind:key="item.id" v-bind:data="item" >
        <button class="btn" v-on:click="buy(item)">В корзину</button>
      </ProductCard>
    </div>
  </div>
</template>

<script>
import ProductCard from '../components/ProductCard.vue'

export default {
  components: { ProductCard },
  name: 'Home',
  computed: {
    catalog() {
      return this.$store.getters.getCatalog
    }
  },
  methods: {
    buy(item) {
      this.$store.dispatch('addToCart', item)
    }
  }
}
</script>

<style>
  .product-list {
    display: flex;
  }

  .btn {
    background: transparent;
    padding: 10px;
    margin: 20px;
    border: 1px solid black;
  }

  .btn:hover {
    color: white;
    background: black;
  }
</style>