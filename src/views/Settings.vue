<template lang="pug">
  .container.Settings
    navbar
    .columns
      section.column.AddOption
        label.label.AddOption__label(for="yourway") I Unstick by:
        .field.has-addons
          .control
            input.input.AddOption__input(
              v-model="newOption"
              type="text",
              name="yourway"
              v-on:keyup.enter="addOption"
            )
          .control
            button.button.is-primary.AddOption__add(
              v-on:click="addOption"
            ) ADD
      section.column
        ul.OptionsList Your mobilizers:
          transition-group(name="OptionsList")
            li.OptionsList__item.has-text-dark.is-size-4.has-text-left(
              v-for="option in options" :key="option"
            ) {{ option }}
              button.OptionsList__delete.delete.is-pulled-right(
                v-on:click="deleteOption(option)"
              )
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

<style scoped lang="scss">

.Settings {
  margin-left: 5px;
}

.AddOption {
  &__label {
    text-align: left;
  }
}

.OptionsList {

  border-left: 1px black;

  &-enter-active, &-leave-active {
    transition: all .3s ease-in;
  }

  &-enter, &-leave-to {
    opacity: 0;
    height: 0;
    transform: rotateY(-90deg);
  }


  &__item {
    padding-left: 5px;
    height: 100%;
  }
  &__item:hover {
    border-bottom: 0 none;
    box-shadow: 0 1px 5px rgba(0, 0, 0, 0.46);
  }

  &__delete {
    vertical-align: middle;
    margin-right: 5px;
    margin-top: 8px;
  }
}

</style>
