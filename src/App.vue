<template>
  <div id="app">
    <form >
      <input type="text" v-model="title" class="todo-input" placeholder="Enter Todo here and click + button...">
      <button @click="AddTodo" class="add-todo" :class="{disableaddtodo: title===''}" :disabled="title === ''">+</button>
      <todolist 
      :todos="todos"
      :deleteTodo="deleteTodo"/>
    </form>
  </div>
</template>

<script>
import todolist from './components/todolist.vue'

export default {
  name: 'app',
  components: {
    todolist
  },
  data(){
    return{
      title: '',
      todos:[
        {
        id: 0,
        title: 'todoOne',
        completed: false
        },
        {
        id: 1,
        title: 'todoTwo',
        completed: true
        },
        {
        id: 2,
        title: 'todoThree',
        completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id);
    },
    AddTodo(e){
      e.preventDefault();
      var nextid = this.todos.length;
      let newTodo = {"id": nextid, "title": this.title, "completed": false}
      this.todos = [...this.todos, newTodo];
      this.title = '';
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.todo-input{
  width: 300px;
  margin-right: 5px;
}
.add-todo{
  background:lightgreen;
  border: none;
  padding: 5px 9px;
  cursor: pointer;
  width: 30px;
}
.disableaddtodo{
  background:lightgrey;
  border: none;
  padding: 5px 9px;
  cursor: not-allowed;
}
</style>
