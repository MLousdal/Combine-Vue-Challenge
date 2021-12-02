<template>
  <div class="sidebar">
    <ul>
      <!-- Using conditional classes based on the content of the review -->
      <li
        v-for="review in reviews"
        :key="review.id"
        :class="[
          review.review == 'like' ? 'like' : '',
          review.review == 'dislike' ? 'dislike' : '',
          review.review == 'neutral' ? 'neutral' : '',
        ]"
      >
        {{ review.name }}
      </li>
    </ul>
    <button @click="$emit('resetReviews')">Nulstil</button>
  </div>
</template>

<script>
export default {
  name: "VueSidebar",
  props: {
    reviews: Array,
  },
  emits: ["resetReviews"],
  computed: {
    reviewTypeStyle() {
      return {
        like: this.reviews.review == "like",
      };
    },
  },
};
</script>

<style lang="scss" scoped>
ul {
  border-radius: 10px;
  border: 1px solid #c4c4c4;
  box-sizing: border-box;
  height: 100%;
  max-height: 262px;
  overflow-y: scroll;
  padding: 0.5rem;
  width: 100%;

  li:not(:first-child):not(:last-child) {
    margin-block: 0.5rem;
  }
}

.sidebar {
  display: flex;
  flex-direction: column;
  gap: 1rem;

  button {
    background: #259a1a;
    border-radius: 20px;
    border: none;
    padding: 0.5rem 1.5rem;
    width: fit-content;
    align-self: flex-end;
    color: #fff;
    font-weight: bold;
    font-size: 14px;
    line-height: 24px;
    cursor: pointer;
  }

  .like {
    color: rgba(37, 154, 26, 1);
  }
  .dislike {
    color: rgba(191, 43, 33, 1);
  }
  .neutral {
    color: rgba(168, 153, 20, 1);
  }
}
</style>
