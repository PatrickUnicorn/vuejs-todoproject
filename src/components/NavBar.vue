<script setup></script>

<template>
  <nav class="navbar">
    <ul class="nav">
      <li class="nav__item">Todo app</li>
    </ul>
  </nav>
</template>

<style scoped>
.navbar {
  width: 100%;
  height: 10rem;
}

.nav {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
  text-align: center;
}

.nav__item {
  display: inline-block;
  list-style-type: none;
  font-size: 3.5rem;
  font-weight: bold;
}
</style>
