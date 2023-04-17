<script setup>
import HelloWorld from './components/HelloWorld.vue'
import GMap from './components/GMap.vue'
import RestaurantList from './components/RestaurantList.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="Eat Map" />
    </div>
  </header>

  <main>
    <div class="wrapper">
      <div class="left">
        <RestaurantList />
      </div>
      <div class="right">
        <GMap />
      </div>
    </div>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

.wrapper {
  display:flex;
  justify-content:space-between;
}

.left {
  width: 50%;
  height: 100vh;
}

.right {
  width: 50%;
  height: 100vh;
}
</style>
