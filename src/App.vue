<template>
  <Header />
  <Main />
  <Footer />
</template>

<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Main from './components/Main.vue';
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500&display=swap');

* {
  font-family: 'Poppins', sans-serif;
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
body {
  margin: 0;
  font-size: 16px;
  font-weight: 400;
  background-color: #001a33;
  color: #dbdbdb;
}
a {
  text-decoration: none;
  color: #ffcc00;
  transition: color .3s ease;
}
a:hover {
  color: #ffd633;
}
h1, h2, h3, h4 {
  font-weight: 500;
}
img {
  max-width: 100%;
  height: auto;
}
.container {
  width: 90%;
  max-width: 480px;
  margin: 0 auto;
}
::-webkit-scrollbar {
    width: .625rem;
    background-color: #D5D5D5;
    border-radius: .5rem;
}
::-webkit-scrollbar-thumb {
     background-color: #727272;
     border-radius: .5rem;
}
::-webkit-scrollbar-thumb:hover {
    background-color: #626262;
}
</style>
