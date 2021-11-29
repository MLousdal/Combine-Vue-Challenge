<template>
  <header>
    <div class="wrapper">
      <span class="logo">24Super</span>
      <div class="header-right">
        <address>Havnepladsen 50, 1234 Aalby</address>
        <nav>
          <a href="#">Forside</a>
          <a href="#" class="active">Besøgsoplevelse</a>
          <a href="#">Find butik</a>
          <a href="#">Kontakt</a>
        </nav>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped lang="scss">
header {
  background: linear-gradient(180deg, #118b24 0%, #149d2a 100%);
  color: white;
  padding: 1rem;

  .wrapper {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;

    .header-right {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      align-items: flex-end;
    }
  }
}

.logo {
  font-family: Lobster;
  font-style: normal;
  font-weight: normal;
  font-size: 60px;
  line-height: 75px;
}

nav {
  display: flex;
  flex-direction: row;
  gap: 3rem;

  a {
    font-family: Source Sans Pro;
    font-style: normal;
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;
    text-align: right;
    text-decoration: none;
    color: inherit;

    &.active {
      text-decoration: underline;
    }
  }
}
</style>
