<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data(){
    return {
      todos: []
    }
  },
  methods:{
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
      .then(res=> this.todos = this.todos.filter(todo=> todo.id !== id))
      .catch(err=>console.log(err))
    },
    addTodo(newTodo){
      const { title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/posts', { title, completed})
      .then(res=> this.todos = [...this.todos, res.data])
      .catch(err=>console.log(err))
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
    .then(res=> this.todos = res.data)
    .catch(err=>console.log(err))
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
   font-family: Avenir, Helvetica, Arial, sans-serif;
   line-height: 1.4;
   background-color: #57B883;
   padding: 10px;
}

#app{
  width: 600px;
  margin: auto;
}



</style>
