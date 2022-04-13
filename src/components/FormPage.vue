<template>
      <div class="checkout"> <!-- if the checkout button is pressed, the page changes using v-else -->
        <div class="checkoutHeader">
          <h2 style="font-family: 'Roboto Condensed'; padding-top: 10px; padding-left: 10px;" class="checkoutText">
            Checkout</h2>

        </div>

        <div class="checkoutMain"> <!-- main container including forms and cart items -->

          <div class="checkoutInfo">
            <form id="customerForm">
              <table>
                <tr>
                  <td>
                    <p><b>Name:</b></p>
                  </td>
                  <td><input type="email" class="form-control" id="formName"></td>
                </tr>
                <tr>
                  <td>
                    <p><b>Phone:</b></p>
                  </td>
                  <td><input type="email" class="form-control" id="formPhone"></td>
                </tr>
                <tr>
                  <td colspan=2><button type="button" class="btn btn-success"
                  @click = "formValidity(cart)">Checkout</button></td>
                </tr>
              </table>
                <h3>Added products</h3>

            </form>
          </div>

          <div class=style id="addedItems">

              <div class="card" style="width: 18rem;" v-for = '(product, index) in cart' :key = "index"> 
              <img v-bind:src="product.img" class="card-img-top">
              <div class="card-body">
                <h5 class="card-title">Subject: {{product.title}}</h5>
                <p class="card-text">Price: ${{product.price}}</p>
                <button @click = "cart.splice(index,1)">Delete</button>

              </div>
            </div>

          </div>

        </div>
      </div>
</template>

<script>
export default {
  name: "FormPage",
  props: ['cart'],
  data() {
    return {
      name: "",
      address: "",
    };
  },

  methods: {
         //validation function to check the user's input
        formValidity(cart) {

          let regName = /^[a-zA-Z]+$/; // regular expression for alphabets
          let regPhone = /^[0-9]+$/; //regular expression for numbers
          let name = document.getElementById('formName').value;
          let phone = document.getElementById('formPhone').value;

          if (!regName.test(name)) {
            alert('Please enter your name (in letters)');
            document.getElementById('name').focus();
            return false;
          }

          else if (!regPhone.test(phone)) {
            alert('Please enter your phone number (in numbers)');
            document.getElementById('phone').focus();
            return false;

          }

          else {
            alert('Your order has been placed successfully!');
            document.getElementById('formName').value = "";
            document.getElementById('formPhone').value = "";
            this.$emit('checkout', cart);
          }
        },
  },
};
</script>