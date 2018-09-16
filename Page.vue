<template>
  <div>
    <article id="page-wrap" class="content-container" :class="{distractionFree, dark}">
      <Content />
    </article>
  </div>
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

<style>
article.content-container {
  display: block;
  width: calc(100vw - 4rem);
  max-width: 40rem;
  margin: auto;
  padding: 0 2rem;
}
article.content-container h1,
article.content-container h2,
article.content-container h3 {
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
