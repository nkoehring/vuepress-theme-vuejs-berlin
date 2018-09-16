<template>
  <div id="home">
    <article class="container">
      <header>
        <h1>Vuejs // Berlin</h1>
        <p>Berlins community around the <a href="https://vuejs.org">Vue Framework</a> and its ecosystem.</p>
      </header>

      <p>
        Vue is an progressive, approachable, versatile and performant
        JavaScript framework. If you're not sure what all this means or how it
        can help you, check out the Vue homepage or visit our meetup. We're
        happy to help you out!
      </p>

      <IndexSection name="Meetups & Talks" path="/meetups/" :newest="newestMeetup">
        Out meetups take place monthly every second Tuesday at 7pm. We usually
        have at least one talk right after we ate some pizza and had some
        drinks. We also <Link href="https://www.instagram.com/vuejs_berlin/">stream</Link>
        and <Link href="https://www.youtube.com/channel/UClSmiKom-8XsWbi5NTWurjg">record</Link>
        the talks every time. Records are usually available one or two days after the meetup.
      </IndexSection>

      <IndexSection name="Newsletters" path="/newsletters/" :newest="newestNewsletter">
        Shortly after every meetup we publish newsletters to help you keeping
        up with all the events in and around the community.
      </IndexSection>

      <IndexSection name="Jobboard" path="/jobs/" :newest="newestJob">
        In future we want to offer a job board with local job opportunities. Stay tuned!
      </IndexSection>

      <SiteFooter />
    </article>
  </div>
</template>

<script>
import IndexSection from './IndexSection'
import Link from './Link'
import SiteFooter from './SiteFooter'

export default {
  components: { IndexSection, Link, SiteFooter },
  computed: {
    newestNewsletter () {
      return this.$site.pages.filter(page => page.path.match(/^\/newsletters\/.+\.html/)).reverse()[0]
    },
    newestMeetup () {
      return this.$site.pages.filter(page => page.path.match(/^\/meetups\/.+\.html/)).reverse()[0]
    },
    newestJob () {
      return this.$site.pages.filter(page => page.path.match(/^\/jobs\/.+\.html/)).reverse()[0]
    }
  }
}
</script>

<style>
#home {
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-evenly;
  height: 100%;
  margin-top: 100vh;
  background: white;
}

#home > .container {
  width: 100%;
  max-width: 900px;
  margin: auto;
  padding: 30px;
}

#home > footer {
  margin-top: 2em;
  font-size: 1rem;
  text-align: right;
}

#home h2 {
  margin-top: 2em;
  font-size: 1.2rem;
}
</style>

