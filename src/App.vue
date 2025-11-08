<template>
  <div id="app">
    <Navbar />
    <main>
      <Convertidor />
    </main>
  </div>
</template>

<script>
  import Navbar from "./components/Navbar.vue"
  import Convertidor from "./components/Convertidor.vue"

  export default {
    components: { Navbar, Convertidor }
  }
</script>

<style>
  #app {
    font-family: 'Segoe UI', sans-serif;
    text-align: center;
    background: #1e1e1e;
    color: #fff;
    min-height: 100vh;
  }

  main {
    padding: 40px;
  }
</style>
