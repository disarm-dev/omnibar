<template>
  <div>
    <div v-for="item in items" :style="{'background-color': 'blue'}">
      {{item.name}}
    </div>
    <auto-input @select="add_item"></auto-input>
  </div>
</template>

<script>
  import AutoInput from './AutoInput.vue'

  export default {
    name: 'app',
    components: {AutoInput},
    data() {
      return {
        items: []
      }
    },
    methods: {
      add_item(item) {
        this.items.push(item)
      }
    }
  }
</script>

<style>
  ul {
    list-style-type: none;
    padding-left: 0;
  }

  li {
    padding: 0.25em 0;
  }
</style>
