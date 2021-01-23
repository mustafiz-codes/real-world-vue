<template>
  <div class="home">
    <SingleProduct msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src

import SingleProduct from "../components/SingleProduct"

export default {
  name: "Home",
  components: {
    SingleProduct,
  },
}
</script>
