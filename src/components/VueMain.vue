<template>
  <div class="wrapper">
    <main>
      <form @submit.prevent="submitReview">
        <input
          type="text"
          required
          placeholder="Dit navn"
          v-model="currentName"
        />
        <div class="btns">
          <div class="btn">
            <button class="red" @click.prevent="submitReview('dislike')">
              <span class="material-icons md-48">sentiment_dissatisfied</span>
            </button>
            <div class="btn-counter">{{ dislikes.length }}</div>
          </div>
          <div class="btn">
            <button class="yellow" @click.prevent="submitReview('neutral')">
              <span class="material-icons md-48">sentiment_neutral</span>
            </button>
            <div class="btn-counter">{{ neutrals.length }}</div>
          </div>
          <div class="btn">
            <button class="green" @click.prevent="submitReview('like')">
              <span class="material-icons md-48">sentiment_satisfied</span>
            </button>
            <div class="btn-counter">{{ likes.length }}</div>
          </div>
        </div>
      </form>
    </main>
    <VueSidebar
      class="sidebar"
      :reviews="reviews"
      @resetReviews="resetReviews"
    ></VueSidebar>
  </div>
</template>

<script>
import VueSidebar from "./VueSidebar.vue";

export default {
  name: "Main",
  components: {
    VueSidebar,
  },
  data() {
    return {
      reviews: [
        {
          id: 1,
          name: "Pernille",
          review: "dislike",
        },
        {
          id: 2,
          name: "Mads",
          review: "dislike",
        },
        {
          id: 3,
          name: "Jens",
          review: "neutral",
        },
        {
          id: 4,
          name: "Henrik",
          review: "dislike",
        },
        {
          id: 5,
          name: "Hans",
          review: "like",
        },
        {
          id: 6,
          name: "Søren",
          review: "neutral",
        },
      ],
      currentName: "",
    };
  },
  computed: {
    likes() {
      let reviews = this.reviews;

      reviews = this.reviews.filter((review) => review.review == "like");

      return reviews;
    },
    neutrals() {
      let reviews = this.reviews;

      reviews = this.reviews.filter((review) => review.review == "neutral");

      return reviews;
    },
    dislikes() {
      let reviews = this.reviews;

      reviews = this.reviews.filter((review) => review.review == "dislike");

      return reviews;
    },
  },
  methods: {
    submitReview(review) {
      if (this.currentName != "") {
        let newReview = {
          id: null,
          name: null,
          review: null,
        };

        newReview.id = this.reviews.length + 1;
        newReview.name = this.currentName;
        newReview.review = review;

        this.currentName = "";
        this.reviews.push(newReview);
      } else {
        alert("Udfyld venligst et navn")
      }
    },
    resetReviews() {
      this.reviews = [];
    },
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  display: grid;
  grid-template-columns: 12rem auto 12rem;
  margin-top: 2rem;
  gap: clamp(1rem, 2.5vw, 5rem);
}

.sidebar {
  grid-column: 3;
  align-self: stretch;
}

main {
  align-items: center;
  display: flex;
  flex-direction: column;
  gap: clamp(1rem, 3.5vw, 3rem);
  grid-column: 2;

  form {
    align-items: center;
    display: flex;
    flex-direction: column;
    gap: clamp(1rem, 2.5vw, 2rem);

    input {
      background: #ffffff;
      border-radius: 10px;
      border: 1px solid #c4c4c4;
      box-sizing: border-box;
      max-width: 50ch;
      padding: 1rem 1.5rem;
    }

    .btns {
      display: flex;
      flex-direction: row;
      gap: clamp(1rem, 2.5vw, 2rem);
    }

    .btn {
      align-items: center;
      display: flex;
      flex-direction: column;
      gap: clamp(1rem, 2.5vw, 2rem);

      button {
        background: none;
        border-radius: 100%;
        border: none;
        color: white;
        cursor: pointer;
        padding: clamp(1rem, 2.5vw, 2rem);
        width: 100%;

        &.red {
          background: rgba(191, 43, 33, 1);
        }
        &.yellow {
          background: rgba(168, 153, 20, 1);
        }
        &.green {
          background: rgba(37, 154, 26, 1);
        }

        span {
          font-size: 64px;
        }
      }

      .btn-counter {
        border-radius: 100%;
        border: 1px solid #c4c4c4;
        color: #c4c4c4;
        font-size: clamp(1.2rem, 2.5vw, 4rem);
        line-height: 24px;
        padding: clamp(0.7rem, 2vw, 1.5rem);
        width: 25px;
        height: 25px;
        text-align: center;
      }
    }
  }
}

@media screen and (max-width: 1100px) {
  .wrapper {
    grid-template-columns: 1fr;
  }

  .sidebar {
    grid-column: 1;
    grid-row: 2;
  }

  main {
    grid-column: 1;
    grid-row: 1;
  }
}
</style>
