<template>
  <header>
    <router-link class='go-home' to="/"><Logo /></router-link>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
import Logo from './Logo.vue'

export default {
  components: { Logo },
  props: {
    title: String
  }
}
</script>

<style scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 4.0rem;
  background: #F7F7F7;
  border-bottom: 4px solid #F0F0F0;
}
header > h1 {
  display: inline-block;
  margin: 0;
  padding: 1em 1rem;
  line-height: 1em;
  font-size: 1.5rem;
  vertical-align: top;
}
header .go-home {
  display: inline-block;
  height: 4rem;
  padding: .5rem 1rem;
}
header .go-home > svg#logo {
  width: 3rem;
  height: 3rem;
}
</style>
