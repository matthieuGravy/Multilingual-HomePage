<script>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";

export default {
  name: "AnimationTitre",
  setup() {
    const message = ref("");
    onMounted(() => {
      const titleElement = document.querySelector(".job");
      const tlGraf = gsap.timeline({ repeat: -3 });
      tlGraf.to(titleElement, {
        y: "0",
        opacity: 1,
        duration: 1,
        ease: "power4.easeInOut",
        onComplete: () => {
          message.value = "JavaScript";
        },
      });

      tlGraf.to(titleElement, {
        y: "0",
        opacity: 1,
        duration: 0.5,
        ease: "power4.easeInOut",
        onComplete: () => {
          message.value = "TypeScript";
        },
      });
      tlGraf.to(titleElement, {
        y: "0",
        opacity: 1,
        duration: 1,
        ease: "power4.easeInOut",
        onComplete: () => {
          message.value = "React";
        },
      });
      tlGraf.to(titleElement, {
        y: "0",
        opacity: 1,
        duration: 0.5,
        ease: "power4.easeInOut",
        onComplete: () => {
          message.value = "Vue";
        },
      });
    });

    return {
      message,
    };
  },
};
</script>
<template>
  <h2 class="job">
    {{ message }}
  </h2>
</template>

<style scoped lang="scss">
.job {
  font-size: 3.5rem;
  max-width: 380px;
  display: flex;
  text-align: center;
  @media screen and (min-width: 950px) {
    max-width: 90%;
    font-family: "Rajdhani", sans-serif;
    font-size: 7rem;
    font-weight: bold;
    text-transform: uppercase;
    letter-spacing: 4px;
    text-align: center;
  }
}
</style>
