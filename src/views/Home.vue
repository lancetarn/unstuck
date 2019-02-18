<template lang="pug">
  div.container
    section
      navbar
    section
      stuck
</template>

<script>
// @ is an alias to /src
import Stuck from '@/components/Stuck.vue'
import Navbar from '@/components/Navbar.vue'

export default {
  name: 'home',
  components: {
    Navbar,
    Stuck
  }
}
</script>
