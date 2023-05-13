<template>
  <div class="square-rating">
    <p v-for="(item, index) in activeRating" :key="index">
      <svg
        width="18"
        height="18"
        viewBox="0 0 18 18"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <circle cx="9" cy="9" r="9" :fill="color" />
      </svg>
    </p>
    <p v-for="(item, index) in deactiveRating" :key="index">
      <svg
        width="18"
        height="18"
        viewBox="0 0 18 18"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <circle cx="9" cy="9" r="8.5" fill="white" :stroke="color" />
      </svg>
    </p>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Rating",
  props: {
    rating: {
      type: Number,
      required: true,
    },
    category: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      maxRating: 5,
      activeRating: [...new Array(Math.ceil(this.rating))],
      deactiveRating: [...new Array(5 - Math.ceil(this.rating))],
      men: "men's clothing",
      women: "women's clothing",
      color: "",
    };
  },
  methods: {
    getColor() {
      if (this.category === this.men) {
        this.color = "#002772";
      } else if (this.category === this.women) {
        this.color = "#720060";
      } else {
        this.color = "#1E1E1E";
      }
    },
  },
  mounted() {
    this.getColor();
  },
};
</script>