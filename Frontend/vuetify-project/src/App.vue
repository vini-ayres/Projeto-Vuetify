<template>
  <router-view />
  <div>
    <Home />
  </div>
</template>

<script>
import Home from './views/Home.vue';
import Default from './layouts/default/Default.vue';
import AppBar from './layouts/default/AppBar.vue';

export default {
  name: 'App',
  components: {
    Home,
    Default,
    AppBar
  }
}
</script>

<style scoped>
</style>
