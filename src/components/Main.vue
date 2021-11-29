<template>
  <div class="wrapper">
    <main>
      <form>
        <input type="text" required placeholder="Dit navn" />
        <div class="btns">
          <div class="btn">
            <button class="red">
              <span class="material-icons md-48">sentiment_dissatisfied</span>
            </button>
            <div class="btn-counter">{{ dislikes.length }}</div>
          </div>
          <div class="btn">
            <button class="yellow">
              <span class="material-icons md-48">sentiment_neutral</span>
            </button>
            <div class="btn-counter">{{ neutrals.length }}</div>
          </div>
          <div class="btn">
            <button class="green">
              <span class="material-icons md-48">sentiment_satisfied</span>
            </button>
            <div class="btn-counter">{{ likes.length }}</div>
          </div>
        </div>
      </form>
    </main>
    <Sidebar class="sidebar"></Sidebar>
  </div>
</template>

<script>
import Sidebar from "./Sidebar.vue";

export default {
  name: "Main",
  components: {
    Sidebar,
  },
  data() {
    return {
      dislikes: ["Henrik", "Mads", "Pernille"],
      neutrals: ["Jens", "Søren"],
      likes: ["Hans"],
    };
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  display: grid;
  grid-template-columns: 12rem auto 12rem;
  margin-top: 2rem;
  gap: 5rem;
}

.sidebar {
  grid-column: 3;
  align-self: stretch;
}

main {
  align-items: center;
  display: flex;
  flex-direction: column;
  gap: 3rem;
  grid-column: 2;

  form {
    align-items: center;
    display: flex;
    flex-direction: column;
    gap: 2rem;

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
      gap: 3rem;
    }

    .btn {
      align-items: center;
      display: flex;
      flex-direction: column;
      gap: 2rem;

      button {
        background: none;
        border-radius: 100%;
        border: none;
        color: white;
        cursor: pointer;
        padding: 2rem;
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
        font-size: 48px;
        line-height: 24px;
        padding: 1.5rem;
        width: fit-content;
      }
    }
  }
}
</style>
