<template>
  <Header />

  <!-- TODO: delete before build -->
  <div style="height: 300vh;"></div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: 'PT Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
button,
input {
  font-family: 'PT Sans', sans-serif;
}
</style>
