<script setup>
import { onMounted, onUnmounted } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import { gsap } from 'gsap'

let previousScrollY = 0
let headerHidden = false

const handleScroll = () => {
  const currentScrollY = window.scrollY

  if (currentScrollY > previousScrollY && !headerHidden) {
    headerHidden = true
    gsap.to('header', { top: '-200px', duration: 0.3 })
  } else if (currentScrollY < previousScrollY && headerHidden) {
    headerHidden = false
    gsap.to('header', { top: '0', duration: 0.3 })
  }

  previousScrollY = currentScrollY
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>
<template>
  <header>
    <div class="logo">
      <img src="src/assets/images/itsgravytrans-2.png" alt="logo de itsgravy" />
    </div>
    <nav>
      <RouterLink to="/">Home</RouterLink>
    </nav>
    <div class="social">
      <a href="https://www.linkedin.com/in/matthieugravy/"
        ><img src="../src/assets/images/in.png" alt="linkedin"
      /></a>
      <a href="https://pommepatate.be/"
        ><img src="../src/assets/images/guyteub.png" alt="pommepatate"
      /></a>
    </div>
  </header>
  <main>
    <RouterView />
  </main>
</template>

<style scoped lang="scss">
header {
  //background-color: rgb(32, 32, 32);
  width: 100%;
  line-height: 1.5;
  display: flex;
  flex-direction: row;
  background-color: black;
  position: fixed;
  top: 0;
  z-index: 10;

  .logo {
    margin: auto;
    flex: 1;
    img {
      padding-left: 2rem;
      height: 5vh;
    }
  }
  .social {
    flex: 1;

    margin: auto;
    display: flex;
    flex-flow: row-reverse;
    padding-right: 2rem;
    img {
      margin: auto;
      padding: 0.5rem;
      height: 5vh;
    }
  }
  nav {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    a {
      padding: 1rem 2rem;
      display: inline-block;
      border-left: 1px solid var(--color-border);
      .router-link-exact-active:hover {
        background-color: transparent;
      }
      .router-link-exact-active {
        color: var(--color-text);
      }
      &::first-of-type {
        border: 0;
      }
    }
  }
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
  }
  .logo {
    margin: 0 2rem 0 0;
  }

  .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
