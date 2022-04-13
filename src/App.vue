<template>
  <div id="app">
    <header>
      <nav class="navbar navbar-dark bg-dark">
        <div class="container-fluid">
          <a class="navbar-brand"><strong>Activity Clubs</strong></a>

          <button class="btn btn-light" v-on:click="showCheckout">
            {{ cartItemCount }}
            <!-- Displaying the number of items added in cart -->
            <span class="fas fa-cart-plus"></span> Checkout
          </button>
        </div>
      </nav>

    </header>
    <div v-if="showSubjects">
      <productList @addProduct="addToCart"></productList> <!-- child component -->
    </div>

    <div v-else>
      <checkoutPage :cart="cart" @checkout="checkout"></checkoutPage> <!-- child component -->
    </div>
  </div>
</template>

<script>
// importing the child component from the components folder
import productList from "./components/ProductList.vue";
import checkoutPage from "./components/FormPage.vue";

export default {
  name: "app",
  components: {
    productList,
    checkoutPage,
  },
  data() {
    return {
      cart: [],
      showSubjects: true, // property implemented to switch pages
    };
  },
  methods: {
    // showCheckout function checks the value of showSubjects and its condition
    showCheckout() {
      this.showSubjects = this.showSubjects ? false : true;
    },

    // function to push subjects in the cart
    addToCart(product) {
      this.cart.push(product);
    },

    // function to clear the cart array in the checkout after checking out
    checkout() {
      this.cart = [];
    },
  },

  // computed property for calculating the value depending on the state of the app
  computed: {
    // function to return the value
    cartItemCount: function () {
      return this.cart.length;
    },

    // to check if cart is empty or not
    checkCart() {
      return this.cartItemCount > 0;
    },
  },
};
</script>
