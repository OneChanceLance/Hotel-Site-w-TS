<script setup lang="ts">
  import { ref } from 'vue';
  defineProps<{ textbox: string }>();

  const sidebarOpen = ref(false);
  const toggleSidebar = () => {
    sidebarOpen.value = !sidebarOpen.value;
  };
  const closeSidebar = () => {
    sidebarOpen.value = false;
  };
</script>

<template>
  <div class="navigation">
    <div class="logo-container">
      <a href="/">
        <img src="../assets/prlogo.png" class="logo" alt="Logo" />
      </a>
    </div>

    <!-- Hamburger button for mobile -->
    <button class="hamburger" @click="toggleSidebar" aria-label="Open menu">
      <span></span>

      <span></span>
    </button>

    <!-- Desktop menu -->
    <div class="menu">
      <ul>
        <li>Rooms</li>
        <li>About</li>
        <li>Offers</li>
        <li>Contact</li>
        <li class="signin">Sign in</li>
      </ul>
    </div>

    <!-- Sidebar for mobile -->
    <div class="sidebar" :class="{ open: sidebarOpen }">
      <button class="close-btn" @click="closeSidebar" aria-label="Close menu">&times;</button>
      <ul>
        <li @click="closeSidebar">Rooms</li>
        <li @click="closeSidebar">About</li>
        <li @click="closeSidebar">Offers</li>
        <li @click="closeSidebar">Contact</li>
        <li class="signin" @click="closeSidebar">Sign in</li>
      </ul>
      <img class="sidebarLogo" src="./../assets/prlogo.png">
    </div>
    <!-- Overlay for sidebar -->
    <div v-if="sidebarOpen" class="sidebar-overlay" @click="closeSidebar"></div>
  </div>
</template>

<style scoped>
  .navigation {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: 0 2rem;
    min-height: 6em;
    box-sizing: border-box;
    background: transparent;
    position: relative;
    z-index: 10;
  }

  .logo-container {
    flex: 0 0 auto;
    display: flex;
    align-items: center;
  }

  .logo {
    height: 4em;
    padding: 0.5em 0;
  }

  .menu {
    flex: 0 0 auto;
    display: flex;
    align-items: center;
  }

  .menu ul {
    display: flex;
    gap: 3em;
    list-style: none;
    margin: 0;
    padding: 0;
    padding-right: 1rem;
  }

  .menu li {
    cursor: pointer;
    height: 40px;
    width: 60px;
    font-weight: 500;
    transition: color 0.2s, outline 0.2s;
    font-family: 'Geneva', Courier, monospace;
    padding: 0 1em;
    margin: 0 0em;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 8px;
  }

  .menu li:hover {
    color: #e75c00;
  }

  .signin {
    outline: 1.5px solid #ffffff;
    border-radius: 15px;
  }

  /* Hamburger styles */
  .hamburger {
    display: none;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 40px;
    height: 40px;
    background: none;
    border: none;
    cursor: pointer;
    z-index: 10001;
    /* ensure it's above everything */
    color: #ffffff;
    /* black text for button */
    position: relative;
  }

  .hamburger span {
    display: block;
    width: 28px;
    height: 3px;
    margin: 4px 0;
    background: #ffffff;
    /* black hamburger lines */
    border-radius: 2px;
    transition: 0.3s;
    z-index: 3;
  }

  .hamburger span:first-child {
    color: #000000;
    /* if you have text in the first span */
  }

  /* Sidebar styles */
  .sidebar {
    display: none;
  }

  .sidebar.open {
    display: block;
    position: fixed;
    top: 0;
    left: 0;
    width: 70vw;
    max-width: 300px;
    height: 100vh;
    background: rgb(36, 36, 36);

    z-index: 10000;
    /* overlays everything including room search */
    padding: 2rem 1.5rem 1.5rem 1.5rem;
    animation: slideIn 0.2s;
  }

  @keyframes slideIn {
    from {
      transform: translateX(-100%);
    }

    to {
      transform: translateX(0);
    }
  }

  .sidebar ul {
    list-style: none;
    padding: 0;
    margin: 2rem 0 0 0;
    display: flex;
    flex-direction: column;
    gap: 1.5em;

  }

  .sidebar li {
    color: rgb(255, 255, 255);
    font-size: 1.2em;
    padding: 0.5em 0;
    border-bottom: 1px solid #eee;
    outline: 1.5px solid #ffffff;
    border-radius: 8px;
    text-align: center;
    cursor: pointer;
  }

  .sidebarLogo {
    align-self: baseline;
    height: 200px;
    opacity: 3%;
  }

  .close-btn {
    position: absolute;
    top: -0.5rem;
    right: -0.5rem;
    background: none;
    border: none;
    font-size: 2rem;
    cursor: pointer;
    color: #ffffff;
    z-index: 103;
  }

  .sidebar-overlay {

    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.2);
    z-index: 9999;
    /* just below sidebar */
  }

  /* Responsive: show hamburger and sidebar, hide menu on mobile */
  @media (max-width: 800px) {
    .menu {
      display: none;
    }

    .hamburger {
      display: flex;
    }

    .sidebar {
      display: none;
    }

    .sidebar.open {
      display: block;
    }
  }
</style>