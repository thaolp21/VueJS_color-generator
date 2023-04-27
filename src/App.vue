<script setup>
import TheMain from "./components/TheMain.vue";
</script>

<template>
  <header>
    <h2>Color Generator</h2>
  </header>

  <main>
    <TheMain />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
  place-items: center;
  text-align: center;
}
header h2 {
  font-size: 2em;
  font-weight: bold;
}
.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
