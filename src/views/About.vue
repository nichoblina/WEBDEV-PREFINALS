<template>
  <div class="mb-3 text-center" id="checkoutbtn">
    <router-link to="/"><button class="btn btn-danger mb-2" @click="checkout">Checkout</button></router-link>
  </div>
  <div class="mb-3 text-center">
    <h1>Total Price: P{{ parentData[0].price }}</h1>
  </div>
  <div class="col text-center" id="cart" v-for="(cartData, index) in cart_data" :key="cartData.id">
    <div class="card mb-4 text-center justify-content-center">
            <img :src="cartData.img" class="card-img-top mx-auto mt-4" alt="">
            <div class="card-body">
                <p class="mb-2" id="prodname">{{ cartData.name }}</p>
                <p class="mb-4" id="prodname"><span>Price: </span>P{{ cartData.price }}</p>
                <div class="d-grid gap-2 d-md-block">
                      <button class="btn-danger mx-2"  @click="minusCart(index)">-</button>
                      <input type="number" v-model="cartData.quantity" class="text-center">
                      <button class="btn-success mx-2"  @click="plusCart(index)">+</button>
                </div>
                <div class="mb-2 mt-2">
                      <router-link to="/"><button class="btn btn-primary"  @click="remove(index)">Remove Item</button></router-link>
                </div>
            </div>
        </div>
  </div>
</template>

<script>

export default {
  name: 'Cart',

  props: {
    parentData: [],
    appFood: []
  },

  data() {
    return {
      cart_data: Array,
      price: Number
    }
  },

  mounted() {
    this.cart_data = this.parentData.map (cartData => {
      return cartData
    })
  },

  methods: {
    minusCart(index) {
        if (this.cart_data[index].quantity > 1) {
            this.cart_data[index].quantity--
            this.cart_data[index].price -= this.appFood[index].price
        }
        console.log(this.cart_data[index].quantity)
    },
    plusCart(index) {
        if (this.cart_data[index].quantity < this.appFood[index].quantity) {
            this.cart_data[index].quantity++
            this.cart_data[index].price += this.appFood[index].price
        }
        console.log(this.cart_data[index].quantity)
    },
    remove(index) {
      this.$emit('remove', this.cart_data[index].id)
    }

    // checkout(index) {
    //   this
    // }
  }
}

</script>