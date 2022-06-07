<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link to="/products" class="top-bar-link">
        <span>Products</span>
      </router-link>
      <a href="/past-orders" class="top-bar-link">
        <span>Past Orders</span>
      </a>
    </nav>
    <!-- <router-link to="#" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart (0)</span>
    </router-link> -->
  </header>
  <router-view />
  <SideBar
    v-if="showSidebar"
    :toggle="toggleSidebar"
    :cart="cart"
    :inventory="inventory"
    :remove="removeItem"
  />
</template>
<script>
import SideBar from './components/SideBar.vue'
export default {
  components: {
    SideBar
  },
  data () {
    return {
      showSidebar: true
    }
  },
  methods: {
    addToCart (name, index) {
      if (!this.cart[name]) this.cart[name] = 0
      this.cart[name] += this.inventory[index].quantity
      this.inventory[index].quantity = 0
    }
  }
}
</script>
