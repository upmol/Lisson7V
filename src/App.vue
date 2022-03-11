<template>
  <div class="todo">
    <ShopHead></ShopHead>
    <router-view></router-view>
  </div>
</template>

<script>
import ShopHead from './components/ShopHead.vue'

export default {
  components: {
    ShopHead,
  },
  mounted() {
    this.$store.dispatch('loadCatalog')
    this.$store.dispatch('loadCart')
  }
}
</script>

<style lang="scss">
   * {
    margin: 0;
    padding: 0;
  }

  header {
    height: 60px;
    padding: 10px 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 5px 10px #ccc;

    nav {
      a {
        margin-right: 20px;
      }
    }
  }

  .page {
    padding: 30px;
  }
</style>
