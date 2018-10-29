<template>
  <article id="page-wrap" class="content-container" :class="{distractionFree, dark}">
    <Content />
  </article>
</template>

<script>
import SideBar from './SideBar.vue'

export default {
  components: { SideBar },
  data () {
    return {
      distractionFree: false,
      dark: false
    }
  }
}
</script>

<style scoped>
.content-container h1,
.content-container h2,
.content-container h3 {
  margin-top: -4rem;
  padding-top: 5.5rem;
}
h1 > a.header-anchor,
h2 > a.header-anchor,
h3 > a.header-anchor {
  visibility: hidden;
  margin-left: -1.25em;
  font-size: 0.85em;
}

h1:hover > a.header-anchor,
h2:hover > a.header-anchor,
h3:hover > a.header-anchor {
  visibility: visible;
}
</style>
