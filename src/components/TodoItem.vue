<template>
  <li>
    <span v-bind:class="{ done: todo.completed }">
      <input v-on:change="todo.completed = !todo.completed" type="checkbox" />
      <strong>{{ index | addOne }}</strong>
      {{ todo.title | uppercase }}
    </span>
    <button class="delete-button" @click="$emit('remove-todo', todo.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    index: Number,
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    },
    addOne(value) {
      return value + 1;
    },
  },
};
</script>

<style lang='scss' scoped>
li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 2rem;
  margin-bottom: 1rem;
}

.delete-button {
  cursor: pointer;
  background: red;
  color: #fff;
  border-radius: 50%;
  font-weight: bold;
  outline: none;
}

input {
  margin-right: 1rem;
}

.done {
  text-decoration: line-through;
}
</style>