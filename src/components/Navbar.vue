<template lang="pug">
  nav.navbar.has-shadow.UnstuckNav
    .navbar-brand
      .navbar-item
        router-link(to="/") UnStuck
      a.navbar-burger.burger(
        v-bind:class="{ 'is-active': menuActive }"
        v-on:click="toggleMenu"
      )
        span(aria-hidden="true")
        span(aria-hidden="true")
        span(aria-hidden="true")
    .navbar-menu(v-bind:class="{ 'is-active': menuActive }")
      .navbar-start
      .navbar-end
        router-link.navbar-item(to="/settings") Settings
</template>

<script>

function initializeData() {
  return { menuActive: false };
}

function toggleMenu() {
  this.menuActive = ! this.menuActive;
}

export default {
  name: 'Navbar',
  components: {},
  data: initializeData,
  methods: {toggleMenu},
}
</script>

<style scoped lang="scss">

.UnstuckNav {
  margin-bottom: 20px;
}
</style>

