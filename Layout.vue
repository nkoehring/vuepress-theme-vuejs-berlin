<template>
  <div class="theme-container">
    <Header :title="isHome ? $site.title : $page.title" v-if="!isHome || !fresh" />
    <transition name='fade'>
      <div v-if="isHome && fresh" @click="fresh = false" class="greeting">
        <div id="wallpaper" v-lazy-load-bg="wallpaper" />
        <Logo />
        <div class="click-hint animated twice tada">click anywhere</div>
      </div>
      <div class="index-wrapper" v-else-if="isHome">
        <div id="wallpaper" v-lazy-load-bg="wallpaper" />
        <Index />
      </div>
      <Page v-else />
    </transition>
    <footer v-if="isHome">
      <router-link to='/about'>about</router-link>
      © 2017 - today <a href="https://koehr.in">koehr</a>
      —
      Background image "Berlin Skyline Sunset" © 2014 <a href="http://sumfinity.com/">Nico Trinkhaus</a>
    </footer>
  </div>
</template>

<script>
import wallpaper from './wallpaper.jpg'
import Logo from './Logo.vue'
import Index from './Index.vue'
import Page from './Page.vue'
import Header from './Header.vue'
import SideBar from './SideBar.vue'

export default {
  components: { Logo, Header, SideBar, Index, Page },
  data () {
    return { fresh: true, wallpaper }
  },
  computed: {
    isHome () {
      return this.$page.frontmatter.home
    },
    sidebarElements () {
      const headers = this.$page.headers || []
      let output = []
      let pointer // nesting pointer

      headers.forEach(({level, title, slug}) => {
      })
    }
  }
}
</script>

<style src="./animations.css"></style>
<style>
@font-face {
  font-family: 'NoName37';
  src: url('no-name-37.light.woff2') format("woff2"),
       url('no-name-37.light.woff') format("woff"),
       url('no-name-37.light.otf') format("opentype");
}

body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  font-size: 20px;
  font-family: NoName37, sans-serif;
  color: #35495E;
}
a {
  text-decoration: none;
  color: #41B883;
}
a.go-back {
  float: left;
}
p {
  line-height: 1.7em;
}
.theme-container {
  padding-top: 5rem;
}
.greeting #logo {
  position: fixed;
  top: 0;
  z-index: 1;
  display: block;
  width: 100vw;
  height: 40vh;
  margin-top: 30vh;
  transform: scale(1.0) translate(0, 0);
}
#wallpaper {
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
  display: block;
  width: 100vw;
  height: 100vh;
  transition: opacity .5s ease-in;
  opacity: .5;
  background: grey url('./wallpaper-preview.jpg') center no-repeat;
  background-size: cover;
}
.index-wrapper {
  height: calc(100vh - 5rem);
}
.click-hint {
  position: absolute;
  width: 100vw;
  top: 75vh;
  text-align: center;
  color: rgba(255, 255, 255, .5);
}
#wallpaper.lazy-load-progress { filter: blur(5px) saturate(25%); }
#wallpaper.lazy-load-success { opacity: 1; }

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s ease;
}
.fade-enter, .fade-leave-active {
  opacity: 0
}

.theme-container > footer {
  position: absolute;
  top: calc(100vh - 1.6rem);
  width: calc(100vw - .6rem);
  font-size: 1rem;
  text-align: right;
  color: rgba(255, 255, 255, .5);
}
.content-container {
  display: block;
  width: calc(100vw - 4rem);
  max-width: 40rem;
  margin: auto;
  padding: 0 2rem;
}
@media screen and (max-width: 600px) {
  .theme-container > header > h1 {
    font-size: 1em;
  }
  .content-container {
    width: calc(100vw - 2rem);
    padding: 0 1rem;
  }
}
</style>
