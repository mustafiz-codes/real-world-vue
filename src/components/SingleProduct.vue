<template>
  <div id="single-product">
    <div class="cart">
      <p>Cart ({{cart}})</p>
    </div>
    <div class="details">
      <div class="left">
        <img :src="image" />
      </div>
      <!-- <img src="../assets/logo.png" /> -->
      <div class="right">
        <h1>{{contt}}</h1>
        <p v-if="inStock>10">In stock</p>
        <p v-else-if="inStock<10 && inStock>0">Limited</p>
        <p v-else>Out of stock</p>
        <p class="sale" v-show="sale">{{percent}}% off</p>
        <ul>
          <!-- <li v-for="detail in details">{{detail}}</li> -->
          <!-- <li v-for="detail in details">{{ detail }}</li> -->
          <li v-for="detail in details" v-bind:key="detail">{{detail}}</li>
        </ul>

        <div
          v-for="variant in variants"
          v-bind:key="variant.id"
          @mouseover="updateProduct(variant.image)"
          class="colorBox"
          v-bind:style="{backgroundColor: variant.color}"
        ></div>

        <button
          v-on:click="addToCart"
          :disabled="!inStock"
          class="{disabled : !inStock } addToCart"
        >Add to Cart</button>
        <button v-on:click="removeFromCart" class="removeFromCart">Remove from Cart</button>
      </div>
    </div>
  </div>
</template>


<script>
// import { libName } from "libName"
export default {
  // props: {
  //   propName: {
  //     type: Number,
  //   },
  // },

  el: "#single-product",
  data() {
    return {
      inStock: 0,
      contt: "Learning vue instance",
      sale: true,
      percent: 10,
      details: ["80% cotton", "20% polyster", "Half sleve"],
      cart: 0,
      image:
        "https://assets.adidas.com/images/w_600,f_auto,q_auto/0a4e5e0b39f34d69a88cab730101f847_9366/Manchester_United_20-21_Home_Youth_Kit_Red_FM4288.jpg",

      variants: [
        {
          id: "mun-red-01",
          color: "red",
          image:
            "https://assets.adidas.com/images/w_600,f_auto,q_auto/0a4e5e0b39f34d69a88cab730101f847_9366/Manchester_United_20-21_Home_Youth_Kit_Red_FM4288.jpg",
        },
        {
          id: "mun-black-01",
          color: "black",
          image:
            "https://assets.adidas.com/images/w_600,f_auto,q_auto/93ef76d9c61645f29a6cab4a0125a4b9_9366/Manchester_United_20-21_Away_Jersey_Green_EE2378_01_laydown.jpg",
        },
      ],
      // image: "../assets/logo.png",
    }
  },
  methods: {
    addToCart() {
      this.cart += 1
    },
    removeFromCart() {
      if (this.cart > 0) {
        this.cart -= 1
      }
    },
    updateProduct(variantImage) {
      this.image = variantImage
    },
  },
}
</script>

<style>
#single-product {
  padding: 0 15%;
}
.cart {
  padding: 10px;
  background-color: rgb(109, 182, 255);
  width: 40%;
  margin: 5% auto;
}

.details {
  display: flex;
  justify-content: space-around;
}
.left {
  width: 40%;
}
.left img {
  width: 100%;
  border: 1px solid rgb(202, 202, 202);
}
.right {
  text-align: left;
  width: 60%;
  padding-left: 10px;
}
.sale {
  color: red;
}
.colorBox {
  /* background-color: red; */
  width: 25px;
  height: 25px;
  margin: 5px 0;
}
button {
  padding: 10px 20px;
  border: 0;
  color: white;
  cursor: pointer;
  margin: 0px 10px 0px 0px;
}
.addToCart {
  background-color: green;
}
.removeFromCart {
  background-color: rgb(151, 0, 0);
}
.disabled {
  cursor: none;
  background-color: rgb(53, 53, 53);
}
</style>
