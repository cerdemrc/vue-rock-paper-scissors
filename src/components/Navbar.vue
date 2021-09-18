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
    justify-content: center;
    align-items: center;

    &__items {
      display: flex;
      list-style-type: none;

      & li {
        margin: 0 20px;
        font-size: 1.2rem;

        & a {
          color: #fff;
          text-transform: uppercase;
          font-family: "Roboto", sans-serif;
          font-weight: bold;
          text-decoration: none;
          letter-spacing: 0.15em;
          display: inline-block;
          padding: 5px;
          position: relative;
          &:after {
            background: none repeat scroll 0 0 transparent;
            bottom: 0;
            content: "";
            display: block;
            height: 2px;
            left: 50%;
            position: absolute;
            background: #fff;
            transition: width 0.3s ease 0s, left 0.3s ease 0s;
            width: 0;
          }
          &:hover:after {
            width: 100%;
            left: 0;
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

@media screen and (max-width: 370px) {
  .header {
    & .nav__items li {
      font-size: 0.8rem;
    }
  }
}
</style>