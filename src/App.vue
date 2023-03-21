<script setup>
import HelloWorld from './components/HelloWorld.vue'
import NavBar from './components/NavBar.vue'
import ArtRef from './components/ArtRef.vue'
</script>

<template>
  <div class="container">
    <ArtRef/>
    <NavBar class="navbar"/>
  </div>
</template>

<style scoped>
.container {
  width: 100vw;
  margin: 0;
  padding: 0;
  /* background-color: blue; */
  /* padding: 2rem;
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  height: 100vh; */
  /* overflow-y: scroll; */
  /* overflow-x: hidden; */
}
.navbar {
  position: fixed;
  bottom: 0;
  left:0;
  width: 100%;
}
</style>
