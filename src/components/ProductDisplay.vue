<template>
  <div class="products-container row">
    <ProductItem
      v-for="item in items"
      :key="item.id"
      :item="item"
      @add-to-cart="addedToCart"
    />
    <div class="cart-container">
      <span class="cart-title">Cart</span>
      <span class="cart-count">{{ cartCount }}</span>
    </div>
  </div>
</template>

<script>
import Shoe1 from "../assets/shoe-1.jpg";
import Shoe2 from "../assets/shoe-2.jpg";
import Shoe3 from "../assets/shoe-3.jpg";

import ProductItem from "./ProductItem";
export default {
  name: "ProductDisplay",
  components: {
    ProductItem,
  },
  data() {
    return {
      items: [
        {
          id: 1,
          imageUrl: Shoe1,
          name: "Shoe 1",
          price: "$55",
        },
        {
          id: 2,
          imageUrl: Shoe2,
          name: "Shoe 2",
          price: "$65",
        },
        {
          id: 3,
          imageUrl: Shoe3,
          name: "Shoe 3",
          price: "$60",
        },
      ],
      cart: []
    };
  },
  mounted() {},
  methods: {
    addedToCart({ ...payload }) {
      this.cart.push(payload)
      console.log('Cart', this.cart);
    },
  },
  computed: {
    cartCount() {
      return this.cart.length;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.products-container {
  border: 2.5px solid #118ab2;
  border-radius: 1rem;
  position: relative;
  color: #118ab2;
}

.products-container::before {
  content: "<ProductDisplay />";
  font-weight: bold;
  position: absolute;
  top: -5%;
  left: 0;
}
.row {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-start;
  max-width: 720px;
  margin: 0 auto;
  padding: 11rem 4rem 5rem;
}

.cart-container {
  position: absolute;
  right: 2rem;
  top: 2rem;
  font-size: 1.9rem;
  border: 1px solid #118ab2;
  padding: 0.5rem;
  border-radius: 0.5rem;
}

.cart-count {
  margin-left: 0.3rem;
  color: tomato;
}
</style>
