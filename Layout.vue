<template>
  <div class="theme-container" :class="{'with-menu': withMenu}">
    <template v-if="!isHome">
      <Header :title="headerTitle" @logo-click="withMenu = !withMenu" :withMenu="withMenu" />
      <SideBar @click="withMenu = false" />
    </template>

    <div v-if="isHome"  class="greeting">
      <div id="wallpaper" v-lazy-load-bg="wallpaper">
        <Logo />
        <div class="hint animated twice tada">scroll down</div>
        <SiteFooter />
      </div>
      <Index />
    </div>
    <Page v-else />

  </div>
</template>

<script>
import wallpaper from './wallpaper.jpg'
import Logo from './Logo.vue'
import Index from './Index.vue'
import Page from './Page.vue'
import Header from './Header.vue'
import SideBar from './SideBar.vue'
import SiteFooter from './SiteFooter.vue'

export default {
  components: { Logo, Header, Index, Page, SiteFooter, SideBar },
  data () {
    return { wallpaper, withMenu: false, hintMenu: true  }
  },
  mounted () {
    if (localStorage.getItem('no-menu-hint')) this.hintMenu = false
    else localStorage.setItem('no-menu-hint', 1)
  },
  watch: {
    $route () {
      // close menu on route change
      this.withMenu = false
    },
    '$page.frontmatter.home' (isHome) {
      if (!isHome && this.hintMenu) {
        this.withMenu = true
        setTimeout(() => { this.withMenu = false }, 1000)
      }
    }
  },
  computed: {
    isHome () {
      return this.$page.frontmatter.home
    },
    headerTitle () {
      return this.isHome ? this.$site.title : this.$page.title
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
  min-height: calc(100vh - 5rem);
  padding-top: 5rem;
  transition: transform .2s ease;
  transform: translate(0, 0);
}
.theme-container.with-menu {
  transform: translate(260px, 0);
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
.hint {
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

.theme-container > header {
  white-space: nowrap;
}
#wallpaper > footer {
  position: absolute;
  bottom: 0;
  width: 99%;
  font-size: 1rem;
  text-align: right;
  color: rgba(255, 255, 255, .4);
}
article.content-container {
  display: block;
  width: calc(100vw - 4rem);
  max-width: 40rem;
  margin: auto;
  padding: 0 2rem;
}
@media screen and (max-width: 600px) {
  .content-container {
    width: calc(100vw - 2rem);
    padding: 0 1rem;
  }
}
</style>
