<script setup lang="ts">
import navigationBar from './components/navigationBar.vue';
import RoomSearch from './components/RoomSearch.vue';
import frontBanners from './components/frontBanners.vue';
</script>

<template>
  <div class="top-background">
    <navigationBar textbox="Search..." />
    <div class="room-search-wrapper">
      <RoomSearch />
    </div>
  </div>
  <div class="bottom-background">
      <frontBanners />
  </div>

  <div>
    <a href="https://vite.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
</template>

<style scoped>
.top-background {
  position: relative;
  background-image: url('./assets/bedroom.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  width: 100vw;
  min-height: 500px;
  padding-top: 0;
  padding-bottom: 2rem;
  overflow: hidden;
}

.room-search-wrapper {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 2rem; /* Adjust as needed */
  display: flex;
  justify-content: center;
  z-index: 2;
  width: 100%;
  pointer-events: none; /* Allows clicks to pass through except for children */
}

.room-search-wrapper > * {
  pointer-events: auto; /* Enable interaction with RoomSearch */
}

.top-background::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  background: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.55) 0%,
    rgba(0, 0, 0, 0.25) 40%,
    rgba(0, 0, 0, 0) 100%
  );
  z-index: 1;
}

.top-background > *:not(.room-search-wrapper) {
  position: relative;
  z-index: 2;
}

.top-background > .navigation {
  position: relative;
  z-index: 10;
}

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
.bottom-background {

  height: 1000px;
}
</style>
