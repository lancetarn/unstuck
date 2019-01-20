<template lang="pug">
  div.suggestion
    h2 {{ suggested }}
    router-link(to="/") Home
</template>

<script>
function getRandomIndex(arr) {
  const i = Math.floor(Math.random() * (arr.length))
  return arr[i]
}

function mounted() {
  this.$data.suggested = getRandomIndex(this.options)
}

function initializeData() {
  return {
    options: [
      'Take a walk',
      'Do ten jumping jacks',
      'Clean some dishes',
      'Eat something moderately healthy'
    ],
    suggested: ''
  }
}

export default {
  name: 'Unstuck',
  components: {},
  data: initializeData,
  mounted,
}
</script>
