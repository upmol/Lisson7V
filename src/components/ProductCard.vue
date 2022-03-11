<template>
  <div class="card">
        <img :src="data.img" />
        <h3>{{data.title}}</h3>
        <p>({{data.price}}$)</p>
        <div v-if="data.quantity"> 
          <input type="number" v-model="quantity" />
        </div>
        <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  computed: {
      quantity: {
      get() {
        console.log(this.data.quantity)
        return this.data.quantity
      },
      set(value) {
        this.$store.dispatch('setQuantity', {id: this.data.id, quantity: value})
      }
    }
  },
  props: [
    'data'
  ]
}
</script>

<style>
  .card{
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    border: 1px solid black;
    margin: 20px;
  }
</style>