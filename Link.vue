<template>
  <a :href="href" :title="title" target="_blank" rel="noopener"><slot></slot></a>
</template>

<script>
export default {
  props: {
    href: String,
    title: String
  }
}
</script>
