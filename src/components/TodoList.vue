<template>
  <div>
    <p class="tasks">
      Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}
    </p>
    <p class="tasks">
      Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}
    </p>
    <todo
      @delete-todo="deleteTodo"
      @toggle-todo="toggleTodo"
      v-for="(todo, i) in todos"
      :key="i"
      :todo="todo"></todo>
  </div>
</template>

<script type = "text/javascript" >

import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    toggleTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      if (this.todos[todoIndex].done === false) {
        this.todos[todoIndex].done = true;
      } else {
        this.todos[todoIndex].done = false;
      }
    },
  },
};
</script>

<style scooped>
p.tasks {
  text-align: center;
}
</style>
