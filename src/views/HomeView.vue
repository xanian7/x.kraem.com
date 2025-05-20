<template>
  <div class="home">
    <h1> {{ displayText }}</h1>
  </div>
  <video autoplay muted loop id="myVideo">
      <source src="/src/assets/cabin-2.mp4" type="video/mp4">
    </video>
</template>

<script>
import { defineComponent, ref, provide, onMounted } from 'vue';

export default defineComponent ({
  name: 'HomeView',
  components: {

  },
  
  setup() {
    const isDarkMode = ref(false);
    const isNavOpen = ref(false);
    provide('isDarkMode', isDarkMode);
    provide('isNavOpen', isNavOpen);

    const i = ref(0)
    const text = 'x.kraem.com';
    const displayText = ref('');

    onMounted(() => {
      typeWriter();
    });

    const typeWriter = () => {
      let speed = 200;
      if (i.value < text.length) {
        displayText.value += text.charAt(i.value);
        i.value++;
        setTimeout(typeWriter, speed);
      }
    }

    return {
      isDarkMode,
      isNavOpen,
      displayText,
      typeWriter,
    }
  },
})
</script>


<style scoped>
  .home {
    position: absolute;
    font-family: 'tiny5';
    z-index: 1;
    min-width: 15dvw;
    top: 20dvh;
    text-align: center;
    opacity: 1;
    border-radius: 5px;
  }

  h1 {
    font-family: 'tiny5';
    font-size: 70px;
    color: white;
    opacity: 1;
    -webkit-user-select: none; /* Safari */
    -ms-user-select: none; /* IE 10 and IE 11 */
    user-select: none; /* Standard syntax */
  }

  #myVideo {
    position: fixed;
    right: 0;
    bottom: 0;
    min-width: 100dvw;
    min-height: 100dvh;
  }
</style>
