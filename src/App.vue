<template>
    <div id="app"> 
      <Header/>
      <AddTodo v-on:add-todo="addTodo" />
     <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    
    </div>
</template>

<script>

import Header from './components/layouts/header.vue';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo.vue';
import axios from 'axios';

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
        
      ]
    }
      },
      methods: {
        deleteTodo(id) {
          axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
          .then(res => this.todos = this.filter(todo => todo.id !==id, res.data))
            .catch(error => console.log(error));
          
        },
        AddTodo(newTodo) {
          const {title, completed} = newTodo;
          axios.post('https://jsonplaceholder.typicode.com/todos', {
            title,
            completed,
          }
            )
            .then(res => this.todos = [...this.todos, res.data])
            .catch(error => console.log(error));
          
        }
      },
      created() {
        axios
  .get('https://jsonplaceholder.typicode.com/todos?_limit=7')
  .then(response => (this.todos = response.data))
  .catch(error => console.log(error))
        
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

.btn {
  display: inline-block;
  border:none;
  background:#555;
  color:id=#fff;
  padding:7px 20px;
  cursor: pointer;
}
</style>
}