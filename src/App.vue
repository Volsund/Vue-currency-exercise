<template>
  <div id="app">
    <currency-selector />
  </div>
</template>

<script>
import CurrencySelector from "./components/CurrencySelector.vue";

export default {
  name: "App",
  components: {
    CurrencySelector,
  },
};
</script>

<style>
:root {
  --border-color: rgb(80, 80, 80);
  --accent-color: rgb(177, 177, 177);
}
* {
  box-sizing: border-box;
}
#app {
  font-family: "Segoe UI", "Roboto", sans-serif;
  color: #2c3e50;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
