<template>
  <div class="product-item column">
    <p class="product-title">{{ item.title }}</p>

    <img :src="item.imageUrl" :alt="item.title" />

      <span class="product-price">
      {{ item.price }}
    </span>

    <button type="button" class="add-to-cart-button" @click="addToCart(item)">
      Add To Cart
    </button>
  </div>
</template>

<script>
export default {
  name: "ProductItem",
  props: {
    item: Object,
  },
  emits: ["add-to-cart"],
  data() {
    return {};
  },

  methods: {
    addToCart(item) {
      this.$emit("add-to-cart", item);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.column {
  width: 30%;
}

.product-item {
  box-shadow: rgba(0, 0, 0, 0.15) 0px 5px 15px 0px;
  cursor: pointer;
  background-color: #f6f6f6;
  border-radius: 1rem;
  position: relative;
  transition: all 0.2s ease;
}

.product-item::before {
  content: "<ProductItem />";
  position: absolute;
  top: -8%;
  left: 0;
  font-weight: bold;
  color: tomato;
}

.product-item:hover {
  transform: translateY(-10px);
}

.product-title {
  font-size: 1rem;
  font-weight: bold;
  color: tomato;
}


.product-price {
  font-size: 1.25rem;
  color: black;
  font-family: Verdana;
}


.add-to-cart-button {
  cursor: pointer;
  padding: 0.5rem;
  text-transform: uppercase;
  float: right;
  border: 1px solid transparent;
  background-color: #353839;
  color: #fff;
  transition: all 0.1s;
  border-bottom-right-radius: 1rem;
  position: relative;
}

.add-to-cart-button:hover {
  background-color: tomato;
}

.add-to-cart-button::before {
  content: "<AddToCart />";
  position: absolute;
  top: -24px;
  text-transform: capitalize;
  font-size: 0.9rem;
  left: 0;
  font-weight: bold;
  color: #000;
}

img {
  width: 100%;
}
</style>
