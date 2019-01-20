<template>
  <div class="home">
    <Stuck />
  </div>
</template>

<script>
// @ is an alias to /src
import Stuck from '@/components/Stuck.vue'

export default {
  name: 'home',
  components: {
    Stuck
  }
}
</script>
