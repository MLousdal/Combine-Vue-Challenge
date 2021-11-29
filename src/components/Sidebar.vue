<template>
  <div class="sidebar">
    <ul>
      <li>test</li>
      <li>test</li>
      <li>test</li>
    </ul>
    <button>Nulstil</button>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
};
</script>

<style lang="scss" scoped>
ul {
  border: 1px solid #c4c4c4;
  box-sizing: border-box;
  border-radius: 10px;
  padding: 0.5rem;
  overflow-y: scroll;
  width: 100%;
  height: 100%;
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
  }
}
</style>
