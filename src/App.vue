<template>
  <body :class="isDarkMode ? 'dark' : 'light'">
    <NavBar />
    <TopBar></TopBar>
    <RouterView />
  </body>
</template>

<script>
import { defineComponent, ref, provide } from 'vue';
import TopBar from './components/TopBar.vue';
import NavBar from './components/NavBar.vue';

export default defineComponent ({
  name: 'App',
  components: {
    TopBar,
    NavBar,
  },
  
  setup() {
    const isDarkMode = ref(true);
    const isNavOpen = ref(false);
    provide('isDarkMode', isDarkMode);
    provide('isNavOpen', isNavOpen);

    return {
      isDarkMode,
      isNavOpen,
    }
  },
})
</script>

<style scoped>

@font-face {
    font-family: 'tiny5';
    src: url('@/assets/Tiny5-Regular.ttf');
}
.dark {
  background-color: #12111F;
  color: white;
  transition: 0.3s;
}

.light {
  background-color: white;
  color: #121212;
  transition: 0.3s;
}

body {
  width: 100vw;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
}
</style>
