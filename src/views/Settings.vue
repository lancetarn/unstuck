<template lang="pug">
  .container
    navbar
    section
      label.label(for="yourway") Another way to unstick:
      .control
        input.input(v-model="newOption" type="text", name="yourway" v-on:keyup.enter="addOption")
      button.button.is-primary(
        v-on:click="addOption"
        ) ADD
    section
      ul Your mobilizers:
        li(v-for="option in options" :key="option") {{ option }}
          span.has-background-danger.deleter(v-on:click="deleteOption(option)") X
</template>

<script>
import Navbar from '@/components/Navbar.vue'

function data () {
  return {
    newOption: '',
    options: loadOptions() || []
}}

function addOption () {
  const trimmed = this.newOption.trim()
  if (!trimmed) {
    return;
  }
  this.options.push(trimmed);
  this.saveOptions(trimmed);
  this.newOption = '';
}

function deleteOption (option) {
  console.log(option);
  const index = this.options.indexOf(option);
  this.options.splice(index, 1);
  this.saveOptions();
}

function loadOptions () {
  const options = localStorage.getItem('unstuckOptions') || '[]';
  return JSON.parse(options);
}

function saveOptions () {
  localStorage.setItem('unstuckOptions', JSON.stringify(this.options));
}

export default {
  name: 'Settings',
  components: { Navbar },
  data,
  methods: { addOption, deleteOption, saveOptions, loadOptions }
}
</script>

<style>
.deleter {
  cursor: pointer;
  margin-left: 5px;
}
</style>
