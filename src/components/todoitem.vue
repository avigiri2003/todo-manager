<template>
  <div>
    <h3> Todo Items... </h3>
    <b-list-group v-for="todo in todoitem" :key="todo.id" class="todoitem">
        <b-list-group-item :class="{done:todo.completed}">
            <input type="checkbox" :id="todo.id" :checked="todo.completed" @click="markComplete(todo.id)"> {{todo.title}} {{todo.completed}}
            <b-button variant="danger" class="del-button" @click="deleteTodo(todo.id)">X</b-button>
            
        </b-list-group-item>
    </b-list-group>
  </div>

</template>

<script>
export default {
  name: 'todoitem',
  props: {
    todoitem: Array,
    deleteTodo: Function
  },
  methods:{
      markComplete(id){
          this.todoitem[id].completed = !this.todoitem[id].completed;
      }
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
.todoitem{
  margin: 0 0px;
  background-color: rgb(43, 226, 186) !important;
}
.done{
    text-decoration: line-through;
}
.del-button{
  background: red;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
