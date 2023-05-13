<template>
  <div class="produk">
    <div v-if="product === ''" class="not-found">
      <p>This product is unavailable to show</p>
      <button @click="incrementIndex">Next Product</button>
    </div>
    <div v-else class="found">
      <div class="image-produk">
        <img :src="product.image" :alt="product.title" />
      </div>
      <div class="detail-produk">
        <div class="top">
          <h2
            class="title-produk"
            :class="{
              'men-produk': product.category === men,
              'women-produk': product.category === women,
            }"
          >
            {{ product.title }}
          </h2>
          <div class="category-produk">
            <span class="category">{{ product.category }}</span>
            <div class="rating">
              <span>{{ product.rating.rate }}/{{ product.rating.count }}</span>
              <Rating
                :rating="product.rating.rate"
                :category="product.category"
              />
            </div>
          </div>
          <p class="description">
            {{ product.description }}
          </p>
        </div>
        <div class="bottom">
          <span
            class="price-produk"
            :class="{
              'men-produk': product.category === men,
              'women-produk': product.category === women,
            }"
            >${{ product.price }}</span
          >
          <div class="action-produk">
            <button
              class="btn-buy"
              :class="{
                'btn-buy-men': product.category === men,
                'btn-buy-women': product.category === women,
              }"
            >
              Buy Now
            </button>
            <button
              class="btn-next"
              :class="{
                'btn-next-men': product.category === men,
                'btn-next-women': product.category === women,
              }"
              @click="incrementIndex"
            >
              Next Product
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
  
<script>
import Rating from "./Rating.vue";

export default {
  name: "ProductDisplay",
  components: { Rating },
  props: {
    product: {
      type: Object,
      required: true,
    },
    men: {
      type: String,
      required: true,
    },

    women: {
      type: String,
      required: true,
    },
    incrementIndex: {
      type: Function,
      required: true,
    },
  },
};
</script>