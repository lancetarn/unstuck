<template lang="pug">
div.Suggester
  button.button.is-primary(v-on:click="suggest", v-if="!suggested") Get Unstuck
  div.suggestion(v-if="suggested")
    h2 {{ suggested }}
    button.button.is-primary(v-on:click="suggest") More
</template>

<script>

const OPTIONS = [
    'Take a walk',
    'Do ten jumping jacks',
    'Clean some dishes',
    'Eat something moderately healthy'
];

function loadOptions () {
  const options = localStorage.getItem('unstuckOptions') || false;
  return JSON.parse(options);
}

function getRandomIndex(arr) {
  const i = Math.floor(Math.random() * (arr.length))
  return arr[i]
}

function suggest() {
  this.suggested = getRandomIndex(this.options)
}

function mounted() {
  this.suggested = ''
}

function initializeData() {
  return {
    options: loadOptions() || OPTIONS,
    suggested: ''
  }
}

export default {
  name: 'Suggester',
  components: {},
  data: initializeData,
  methods: {suggest},
  mounted,
}
</script>
