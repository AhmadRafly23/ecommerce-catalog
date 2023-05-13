<template>
  <div id="app">
    <div class="overlay"><BackgroundOverlay class="bg-overlay" /></div>
    <div class="content">
      <div v-if="loading" class="loader"></div>
      <ProductDisplay
        v-else
        :product="product"
        :men="men"
        :women="women"
        :incrementIndex="incrementIndex"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import "./assets/style/page.css";
import BackgroundOverlay from "@/components/BackgroundOverlay.vue";
import ProductDisplay from "./components/ProductDisplay.vue";

export default {
  name: "App",
  components: { BackgroundOverlay, ProductDisplay },
  data() {
    return {
      product: {},
      loading: false,
      index: 1,
      men: "men's clothing",
      women: "women's clothing",
    };
  },
  methods: {
    async getData() {
      this.loading = true;
      const response = await axios(
        `https://fakestoreapi.com/products/${this.index}`
      );
      this.product = response.data;
      this.loading = false;
    },
    incrementIndex() {
      this.index = this.index + 1;

      if (this.index > 21) {
        this.index = 1;
      }

      this.getData();
    },
  },
  mounted() {
    this.getData();
  },
};
</script>

