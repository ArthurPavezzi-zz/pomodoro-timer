<template>
  <div id="todo">
    <v-text-field color="white" v-model="newTodo" label="New Todo"/>
    <v-btn class="add-todo" @click="addNewTodo" text>Add New Todo</v-btn>
    <v-btn text @click="removeAllTodos">Remove All</v-btn>
    <v-btn text @click="markAllDone">Mark All Done</v-btn>
    <ul>
      <li v-for="(todo, index) in todos" :key="todo.id" class="todo">
        <h3 :class="{ done: todo.done }" @click="toggleDone(todo)">{{ todo.content }}</h3>
        <v-btn class="remove" text @click="removeTodo(index)">Remove</v-btn>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TaskList",
  data() {
    return {
      newTodo: '',
      todos: []
    }
  },
  methods: {
    addNewTodo() {
      this.todos.push({
        id: Date.now(),
        done: false,
        content: this.newTodo,
      });
      this.newTodo = '';
    },

    toggleDone(todo) {
      todo.done = !todo.done;
    },

    removeTodo(index) {
      this.todos.splice(index, 1);
    },

    markAllDone() {
      this.todos.forEach((todo) => todo.done = true);
    },

    removeAllTodos() {
      this.todos = [];
    }
  }
}
</script>

<style lang="sass" scoped>
#todo
  padding-top: 1em
  padding-bottom: 1em
  font-size: 2em
  width: 50%
  margin: 0 auto
  color: whitesmoke

.add-todo
  display: block
  width: 100%
  font-size: 1em
  padding: 10px
  margin: 0.5em

.v-text-field
  width: 80%
  margin: 0 auto
  color: whitesmoke

li
  display: flex
  flex-direction: column
  width: 80%
  margin: 0 auto

h3
  font-size: 28px

.v-btn
  color: whitesmoke
  width: 100%
  padding: 10px

p
  display: block
  width: 100%
  font-size: 1em
  margin: 0.5em

.v-btn
  margin: 0
  padding: 0

.remove
  width: 100%
  margin: 10px 0 0 0

.todo
  cursor: pointer

.done
  text-decoration: line-through
</style>