<template>
  <div>
    <input type="text" v-model="text" />
    <ul>
      <li v-for="result in results" @click="select_item(result)">
        {{result.name}}
      </li>
    </ul>
  </div>
</template>

<script>

  export default {
    name: 'app',
    data() {
      return {
        text: '',
      }
    },
    computed: {
      results() {
        if (!this.text.length) return []
        return this.options.filter(a => a.name.toLocaleLowerCase().indexOf(this.text.toLocaleLowerCase()) !== -1)
      },
      options() {
        return [
          {name: "Filter name"},
          {name: "Filter date"},
          {name: "Filter id"},
          {name: "Filter type"},
          {name: "Filter description"}
        ]
      }
    },
    methods: {
      select_item(item) {
        this.$emit('select', item)
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
