<template>
    <div id="app"> 
      <Header/>
      <AddTodo/>
     <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    
    </div>
</template>

<script>

import Header from './components/layouts/header.vue';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo.vue';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Do it One",
          completed: false
        },
        {
          id: 2,
          title: "Do it Two",
          completed: false
        },
        {
          id: 3,
          title: "Do it One",
          completed: false
        }
      ]
    }
      },
      methods: {
        deleteTodo(id) {
          this.todos = this.filter(todo => todo.id !==id);
        }
      }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
