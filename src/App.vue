<template>
  <div id="app">
    <home></home>
  </div>
</template>

<script>
import home from './views/Home.vue'

export default {
  name: 'App',
  components: {
    home
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Gothic+A1:wght@300;400;500;600;700;800;900&display=swap');

:root {
  --bg-opacity: 1;
}

* {
  margin: 0;
  padding: 0;
  /* overflow-x: hidden !important; */
}

input:focus,
button:focus,
textarea:focus {
  outline: none;
}

html {
  scroll-behavior: smooth;
}

body {
  font-size: 14px;
  box-sizing: border-box;
  font-family: 'Gothic A1', sans-serif;
  background-color: #0C0C0C;
  color: white;
  height: 100vh;
  scroll-behavior: smooth;
  width: 100%;
  position: relative;
  /* overflow-x: hidden !important; */
}

a {
  color: white;
  text-decoration: none;
}

/* SCROLL BAR */
/* .section-header{
  display: none;
} */
/* width */
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #0C0C0C;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #000001;
}

@media (max-width:991.98px) {
  * {
    overflow-x: hidden !important;
  }

  .section-header {
    padding: 24px 0px;
    display: block;
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 3px;
    z-index: 999999;
    text-align: center;
    background-color: #0C0C0C;
  }
}</style>
