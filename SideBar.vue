<template>
  <ol class="sidebar">
    <li v-for="element in elements">{{ element }}</li>
  </ol>
</template>

<script>
export default {
  props: {
    elements: Array
  }
}
</script>

<style>
</style>
