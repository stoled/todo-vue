<template>
  <li>
    <span v-bind:class='{done: todo.completed}'>
      <input type="checkbox" v-on:change='todo.completed = !todo.completed'>
      <b>{{index + 1}}</b>
      {{todo.title | uppercase}}
    </span>
    <button class="rm" 
            v-on:click="$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    margin: 1rem;
    padding: 1rem;
  }

  .rm {
    border-radius: 50%;
    height: 30px;
    width: 30px;
  }

  .done {
    text-decoration: line-through;
  }
</style>