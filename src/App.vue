<template>
  <div class="container">
    <recursive-circle
      :width="500"
      :border-radius="6"
      :padding="40"
      default-color="#271d4a"
    ></recursive-circle>
  </div>
</template>

<script>
import RecursiveCircle from "./components/RecursiveCircle.vue";

export default {
  name: "App",
  components: { RecursiveCircle },
};
</script>

<style>
.container {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  align-content: center;
  justify-content: center;
  justify-items: center;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body,
html {
  background: grey;
}
</style>
