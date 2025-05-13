<script setup lang="ts">
defineProps<{
  textbox: string
}>()
</script>
<template>
  <div class="navigation">
    <div class="logo-container">
      <a href="/">
        <img src="../assets/logo.png" class="logo" alt="Logo" />
      </a>
      
    </div>
    <div class="textbox">
      <input type="text" placeholder="Search..." />
    </div>
    <div class="menu">
      <ul>
        <li>Home</li>
        <li>About</li>
        <li>Contact</li>
      </ul>
    </div>http://localhost:5173/src/assets/logo.png
  </div>
</template>
<style scoped>
.logo {
  justify-content: left;
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.navigation {
  background-color: #ffffff;
  width: 100vw;
  display: row;
}
</style>