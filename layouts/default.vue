<template>
  <div>
    <NavBar />
    <main>
      <slot />
    </main>
    <Footer />
  </div>
</template>

<script setup>
// Le composant Layout ne nécessite pas de logique supplémentaire
</script>

<style scoped>
main {
  min-height: calc(100vh - 150px);
}
</style> 