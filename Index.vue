<template>
  <div id="home" class="content-container" @click="clickedy">
    <div class="container newsletters">
      <header>NEWS LETTERS</header>
      <ol>
        <li v-for="nl in newsletters"><router-link :to="nl.path">{{ nl.title }}</router-link></li>
      </ol>
      <footer v-if="newsletters.length > 3"><router-link to="/newsletters/">see all</router-link></footer>
      <footer class="empty" v-if="newsletters.length === 0">nothing here yet</footer>
    </div>
    <div class="container meetups">
      <header>MEETUPS TALKS</header>
      <ol>
        <li v-for="mu in meetups"><router-link :to="mu.path">{{ mu.title }}</router-link></li>
      </ol>
      <footer v-if="meetups.length > 3"><router-link to="/meetups/">see all</router-link></footer>
      <footer class="empty" v-if="meetups.length === 0">nothing here yet</footer>
    </div>
    <div class="container jobs">
      <header>JOB BOARD</header>
      <ol>
        <li v-for="j in jobs"><router-link :to="j.path">{{ j.title }}</router-link></li>
      </ol>
      <footer v-if="jobs.length > 3"><router-link to="/jobs/">see all</router-link></footer>
      <footer class="empty" v-if="jobs.length === 0">nothing here yet</footer>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    clickedy () {
      console.log('page n site', this.$page, this.$site)
    }
  },
  computed: {
    newsletters () {
      return this.$site.pages.filter(page => page.path.match(/^\/newsletters\/.+\.html/)).reverse().slice(0,3)
    },
    meetups () {
      return this.$site.pages.filter(page => page.path.match(/^\/meetups\/.+\.html/)).reverse().slice(0,3)
    },
    jobs () {
      return this.$site.pages.filter(page => page.path.match(/^\/jobs\/.+\.html/)).reverse().slice(0,3)
    },
  }
}
</script>

<style>
#home {
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-evenly;
  height: 100%;
}
#home .container {
  position: relative;
  flex: 0 0 auto;
  width: 100%;
  max-width: calc(100vw - 4rem);
  margin: .5rem 0;
  height: 9em;
  background: rgba(255, 255, 255, .8);
  color: #35495E;
  font-weight: bold;
  border: 1px solid #41B883;
  transition: background .3s;
}
#home .container:hover {
  background: rgba(255, 255, 255, 1.0);
}
#home .container > header {
  position: absolute;
  top: 7em;
  left: 0;
  width: 1em;
  height: 1em;
  text-align: center;
  transform: rotate(-90deg);
  transform-origin: top right;
}
#home .container > footer {
  text-align: center;
}
#home .container > footer.empty {
  line-height: 5em;
}
#home .container > ol {
  list-style: none;
  margin: 1em 3em 1em;
}
#home .container li {
  line-height: 1.2em;
  margin: .5em 0;
}
#home .container li > a {
  text-shadow: 0 0 2px white, 0 0 10px white;
}
</style>

