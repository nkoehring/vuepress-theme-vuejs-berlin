<template>
  <nav :style="{width: `${width}px`, left: `-${width}px`}">
    <router-link class="sidebar-home" to="/">
      back to start
    </router-link>
    <ol class="sidebar" v-for="section in sections" v-if="section.title !== 'Job Board'">
      <label>
        <router-link :to="section">{{ section.title }}</router-link>
      </label>
      <li v-for="article in articles" v-if="article.path.indexOf(section.path) === 0">
        <router-link :to="article">{{ article.title }}</router-link>
      </li>
    </ol>
  </nav>
</template>

<script>
import Logo from './Logo.vue'

export default {
  components: { Logo },
  props: {
    width: {
      type: Number,
      default: 260
    }
  },
  computed: {
    pages () {
      return this.$site.pages.map(page => {
        // todo: headers?
        const { title, path } = page
        const trimmed = path.replace(/\/$/, '')
        const level = (trimmed.match(/\//g) || []).length
        return { title, path, level }
      })
    },
    sections () {
      return this.pages.filter(page => page.level === 1)
    },
    articles () {
      return this.pages.filter(page => page.level === 2)
    }
  }
}
</script>

<style scoped>
nav {
  position: fixed;
  top: 0;
  left: -260px;
  display: block;
  width: 260px;
  height: 100vh;
  background: white;
}
ol.sidebar {
  display: block;
  list-style-type: none;
  padding: 0 0 0 1em;
  line-height: 1.2em;
}
ol.sidebar > label {
  font-weight: bold;
  line-height: 2em;
}
ol.sidebar > label > a {
  color: #DDD;
}
.sidebar-home {
  display: block;
  height: 4rem;
  padding: .5rem 1rem;
}
.sidebar-home > svg#logo {
  width: 3rem;
  height: 3rem;
}
</style>
