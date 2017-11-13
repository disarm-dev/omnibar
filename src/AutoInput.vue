<template>
  <div>
    <input type="text" v-model="text" @keyup.up="decrement_index()" @keyup.down="increment_index()" @keyup.enter = "select_item(results[index])"/>
    <ul>
      <li v-for="(result,i) in results" @click="select_item(result)" v-bind:class="{ selected: i==index }">
        {{result.name}}
      </li>
    </ul>
  </div>
</template>

<script>
  /**
   * The auto-input component has a @select event
   */
  export default {
    name: 'app',
    data() {
      return {
        text: '',
        index: 0
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
      },
      increment_index() {
        this.index = this.index == this.results.length ? 0 : this.index + 1;
      },
      decrement_index() {
        this.index = this.index == 0 ? this.results.length : this.index - 1;
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

  .selected {
    color: blue;
  }
</style>
