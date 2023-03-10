<script setup>
import { onMounted, onUnmounted } from "vue";
import gsap from "gsap";
import { MorphSVGPlugin } from "gsap/MorphSVGPlugin";

gsap.registerPlugin(MorphSVGPlugin);

let ctx;
onMounted(() => {
  ctx = gsap.context(() => {
    gsap.to("#large", {
      duration: 1,
      ease: "none",
      repeat: -1,
      yoyo: true,
      delay: 1,
      repeatDelay: 1,
      morphSVG: "m0,0 H256 V256 H0 V0Z"
    });
  });
});

onUnmounted(() => {
  ctx.revert();
});
</script>

<template>
  <div class="container">
    <h1>GSAP + Vue</h1>
    <svg  xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" aria-hidden="true" role="img" class="iconify iconify--logos vue logo"  height="200" preserveAspectRatio="xMidYMid meet" viewBox="0 0 256 256">
      <!-- <path fill="transparent" d="m0,0 H256 V256 H0 V0Z" /> -->
      <path id="large" fill="#41B883" d="m0 0l128 220.8L256 0h-51.2L128 132.48L50.56 0H0Z"></path>
      <path fill="#35495E" d="M50.56 0L128 133.12L204.8 0h-47.36L128 51.2L97.92 0H50.56Z"></path>
    </svg>
  </div>
</template>

<style scoped>
.container {
  margin: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100vh;
}

h1 {
  font-size: 3.2em;
  line-height: 1.1;
}
.logo {
  height: 200px;
  padding: 1.5em;
}
</style>
