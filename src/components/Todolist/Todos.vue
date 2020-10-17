<template>
  <v-container class="todo-app elevation-3 mt-10">
    <h2>Todolist with Local Storage</h2>

    <v-text-field
      class="todo-input"
      v-model="newTodo"
      label="Add todo"
      @keydown.enter="addTodo"
    ></v-text-field>

    <p
      class="todo-item"
      v-for="todo in todos"
      v-bind:class="{ completed: todo.completed }"
      :key="todo.id"
    >
      <input type="checkbox" v-model="todo.completed" />
      {{ todo.text }}
      <v-btn
        class="del"
        color="error float-right"
        elevation="1"
        rounded
        x-small
        fab
        @click="deleteTodo(todo)"
        ><v-icon dark>
          mdi-delete
        </v-icon></v-btn
      >
    </p>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: [],
    };
  },
  methods: {
    addTodo() {
      this.todos.push({ text: this.newTodo, completed: false });
      this.newTodo = '';
    },
    deleteTodo: function(todo) {
      this.todos.splice(this.todos.indexOf(todo), 1);
    },
  },
  mounted() {
    console.log('App mounted!');
    if (localStorage.getItem('todos'))
      this.todos = JSON.parse(localStorage.getItem('todos'));
  },
  watch: {
    todos: {
      handler() {
        console.log('Todos changed!');
        localStorage.setItem('todos', JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
};
</script>

<style scoped>
.todo-app {
  background: rgb(250, 250, 250);

  border-radius: 5px;
}

.completed {
  text-decoration: line-through;
}
.todo-item {
  background-color: #16213e;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
  font-size: 20px;
  color: white;
  border-radius: 5px;
}
.del {
  cursor: pointer;
  top: -2px;
}

.del:hover {
  transform: scale(0.9);
}

.todo-input {
  font-size: 18px;
}
</style>
