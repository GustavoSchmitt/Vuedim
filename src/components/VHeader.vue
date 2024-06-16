<script setup>
import { RouterLink, RouterView } from 'vue-router'
import profiles from '../data/json.json'

defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>

  <header>

    <div class="wrapper">
      <div class="banner">
        <div class="bannerFilter"></div>
        <img alt="Vue logo" class="logo" src="@/assets/logoPudim.png" width="125" height="125" />

        <h1 class="caramel">Doceria Schmitt</h1>
        <h3 class="cheek">
          You’ve successfully created a project with
          <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
          <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
        </h3>

      </div>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>

        <div v-for="profile in profiles">
          <RouterLink :id="profile.id" :key="profile.id" :to="'/profile/' + profile.id">{{ profile.name }} Profile
          </RouterLink>
        </div>

      </nav>
    </div>
  </header>

</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

.header {
  display: flex;
  flex-direction: column;
}

header div {
  width: 100%;
}

.banner {
  text-align: center;
  background-image: url("../assets/kitPudim.png");
  background-size: cover;
  background-position: 50%;
  position: relative;
  width: 100%;
}

.bannerFilter {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: aqua;
  background: radial-gradient(#ffffff00 20%, #FEDC7199 80%);
}



header {
  line-height: 1.5;
  max-height: 100vh;
  background-color: var(--c-white);
  flex-direction: column;
}

header * {
  flex: 1;
}


nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-cheek);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    /* padding-right: calc(var(--section-gap) / 2); */
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
    flex-direction: column;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}

@media (min-width: 1024px) {

  .banner {
    text-align: left;
  }
}
</style>
