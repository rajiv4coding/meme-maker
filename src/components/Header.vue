<template>
  <header class="header">
    <nav class="container navbar">
        <h1 class="nav-brand"><a href="/">Meme Maker</a></h1>
        <p>By : <a href="https://rajiv-singh.web.app" target="_blank">Rajiv Singh</a></p>
    </nav>
  </header>
</template>

<script setup>
  //
</script>

<style>
.header {
  background-color: #00284d;
}
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 64px;
}
.nav-brand {
  color: #034F84;
  font-size: 22px;
  font-weight: 500;
}
.navbar p {
  font-size: 14px;
  font-weight: 500;
}
</style>