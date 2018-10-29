<template>
  <header :class="{'with-menu': withMenu}">
    <div class="logo" @click="$emit('logo-click')">
      <Logo />
    </div>
    <h1 class="title">{{ title }}</h1>
  </header>
</template>

<script>
import Logo from './Logo.vue'

export default {
  components: { Logo },
  props: {
    title: String,
    withMenu: Boolean
  }
}
</script>

<style scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 4.0rem;
  background: #F7F7F7;
  border-bottom: 4px solid #F0F0F0;
}
.title {
  margin: 0;
  padding: 1em 0;
  line-height: 1em;
  font-size: 1.5rem;
  text-align: center;
}
.logo {
  transition: transform .2s ease;
  position: absolute;
  top: 0;
  left: 0;
  height: 4rem;
  padding: .5rem 1rem;
}
.logo > svg#logo {
  width: 3rem;
  height: 3rem;
}

.with-menu .logo {
  transform: rotate(90deg) translate(-10px, 20px);
}

@media screen and (max-width: 780px) {
  .title {
    margin: 0 0 0 72px;
  }
}
</style>
