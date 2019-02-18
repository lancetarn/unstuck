<template lang="pug">
  nav.navbar
    .navbar-brand
      .navbar-item
        router-link(to="/") UnStuck
    .navbar-menu
      .navbar-end
        router-link(to="/settings") Settings
</template>

<script>
export default {
  name: 'Navbar',
  components: {},
  data: function () {return {}}
}
</script>

