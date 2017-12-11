<template>
  <div class='todo'>
    <h2>Todos</h2>
    <ul>
      <li v-for='todo in todolist'>
        {{ todo.id }} - {{ todo.name }} <button v-on:click="remove(todo)">Remove</button>
      </li>
    </ul>
    <div>
      <input type="text" v-model="todo"/>
    </div>
    <div>
      <button v-on:click="add">Add</button> 
    </div>
  </div>
</template>

<script>
import todolistJson from '../../static/data/todolist.json'

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js PWA',
      todolist: todolistJson,
      todo: ''
    }
  },
  methods: {
    add: function () {
      this.todolist.push({id: this.todolist.length + 1, name: this.todo})
      this.todo = ''
    },
    remove: function (todo) {
      this.todolist = this.todolist.filter(function (el) { return el.id !== todo.id })
    }
  }
}
</script>

<!-- Add 'scoped' attribute to limit CSS to this component only -->
<style>
h1, h2 {
  font-weight: normal;
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
  color: #35495E;
}
</style>
