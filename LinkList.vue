<template>
  <section :name="name">
    <header>
      <h2><slot name="header"></slot></h2>
      <p><slot name="tagline"></slot></p>
    </header>
    <ol>
      <li v-for="link in links">
        <router-link :to="link.path">{{ link.title }}</router-link>
      </li>
    </ol>
  </section>
</template>

<script>
export default {
  props: {
    name: String,
    links: Array
  }
}
</script>
