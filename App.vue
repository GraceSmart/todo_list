<template>
  <div class="wrapper">
    <div id="newtodo">
      <input type="text" name="todo-text" v-model.trim="newTodoText"
        id="todo-text" placeholder="New todo">
      <button v-on:click="addTodo()">Add</button>
    </div>
    <ul class="todo" v-if="todos.length">
      <li v-for="todo in todos" :key="todo.id">
        <span>{{ todo.text }}</span>
        <button v-on:click="removeTodo(todo)">Remove</button>
      </li>
    </ul>
    <p class="none" v-else>Add a new todo in the input above</p>
  </div>
</template>

<script>
export default {
    name: 'App',
    components: {
    },
    data () {
        return {
            newTodoText: "",
            todos: []
        }
    },
    methods: {
        addTodo () {
            if (this.newTodoText) {
                
                this.todos.push({
                    text: this.newTodoText,
                    id: Date.now()
                })
                
                this.newTodoText = ''
            }
        },
        removeTodo (item) {
            
            this.todos = this.todos.filter(_item => _item !== item)
        }
    }
}
</script>

<style>
*, *::before, *::after {
  box-sizing: border-box;
}

html, body {
  font: 16px/1.2 BlinkMacSystemFont, -apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  padding: 10px;
}

.wrapper {
  width: 75%;
  margin: 0 auto;
}

#newtodo {
  width: 100%;
}

input {
  width: 90%;
}

button {
  border: 1px solid green;
  background: green;
  color: white;
  font-size: 0.8rem;
  padding: 2px 4px;
  cursor: pointer;
  width: 10%;
}


form #todo-text {
  width: 100%;
  padding: 10px;
  border: 1px solid #777;
}

ul, li {
  margin: 0;
  padding: 0;
}

p.none {
  color: #888;
  font-size: small;
}

.todo li {
  display: flex;
  margin: 5px 0;
}

.todo li span {
  flex: 1;
}


.todo li button {
  border: 1px solid red;
  background: red;
  color: white;
  font-size: 0.8rem;
  padding: 2px 4px;
  cursor: pointer;
}
</style>
