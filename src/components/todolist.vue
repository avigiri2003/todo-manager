<template>
  <div>
    <h3> Todo List </h3>  
    <b-list-group class="todolist">
      <b-list-group-item> 
        <todoitem :todoitem="todos" :deleteTodo="deleteTodo"/> 
      </b-list-group-item>
    </b-list-group>
  </div>

</template>

<script>

import todoitem from './todoitem'

export default {
  name: 'todolist',
   components: {
    todoitem
  },
  props: {
    todos: Array,
    deleteTodo: Function
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.todolist{
  margin: 0 500px;
  background-color: blueviolet !important;
}
</style>
