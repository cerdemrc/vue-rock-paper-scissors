<template>
  <div id="app">
    <Navbar />
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
export default {
  name: "App",
  components: {
    Navbar,
  },
};
</script>

<style lang="scss">
#app {
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  color: white;
  margin-top: 50px;
  font-family: sans-serif;
}
</style>
