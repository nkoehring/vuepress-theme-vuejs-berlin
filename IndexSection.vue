<template>
  <section :id="id" :name="name" class="index-section">
    <header>
      <h2>{{ name }}</h2>
      <p><slot></slot></p>
    </header>

    <p>
      <router-link v-if="newest" :to="newest.path">go to {{ newest.title }}</router-link>
      <br />
      <router-link :to="path">go to {{ name }} archive</router-link>
    </p>
  </section>
</template>

<script>
export default {
  props: {
    name: String,
    path: String,
    newest: Object
  },
  computed: {
    id () {
      return this.name.toLowerCase().replace(/[^a-z0-9-]/g, ' ').replace(/[ ]+/g, '-')
    }
  }
}
</script>

<style>
.index-section > ol {
  list-style-type: none;
}
</style>
