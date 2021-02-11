<template>
  <div class="header">
    <div class="nav">
      <ul class="nav__items">
        <li><router-link to="/" tag="a">Start Game</router-link></li>
        <li><router-link to="/rules" tag="a">Rules</router-link></li>
      </ul>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.header {
  width: 100%;
  height: auto;
  & .nav {
    display: flex;
    justify-content: space-around;
    align-items: center;

    &__items {
      display: flex;
      list-style-type: none;

      & li {
        margin: 0 20px;
        font-size: 1.8rem;

        & a {
          text-decoration: none;
          color: white;
          font-family: "Roboto", sans-serif;
          font-weight: bold;

          &:hover {
            color: springgreen;
          }
        }
      }
    }
  }
}

@media screen and (max-width: 450px) {
  .header {
    & .nav__items li {
      font-size: 1.2rem;
    }
  }
}
</style>