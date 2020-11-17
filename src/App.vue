<template>
    <div>
        <AddToDoItem class="create_todo_form" @add-todo="addToDo"/>
        <ToDoList class="todo_list" v-bind:todos="todos" @remove-todo="removeTodo"/>
    </div>
</template>

<script>
  import ToDoList from '@/components/ToDoList'
  import AddToDoItem from '@/components/AddToDoItem'
  export default {
      name: 'App',
      data() {
          return {
            todos: []
          }
      },
      components: {
          ToDoList, AddToDoItem
      },
      mounted() {
          fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
            .then(response => response.json())
            .then(json => {this.todos = json})
            .catch(error => {throw error})
      },
      methods: {
          removeTodo(id) {
              this.todos = this.todos.filter(t => t.id !== id)
          },
          addToDo(todo) {
             this.todos.push(todo)
          }
      }
  }
</script>

<style>
  
#app {
    height: 80vh;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    margin-bottom: 60px;
    background: #fff;
    border: 5px solid #4e6e41;
    border-radius: 50px;
}

body {
    min-width: 330px;
    min-height: 285px;
    width: 100%;
    height: 100%;
    padding: 0;
    margin: 0;
    overflow: hidden;
    background: url("./media/leafes_for_body_background.jpg");
    background-size: cover;
}

.create_todo_form {
    margin: 3vh auto;
}

.todo_list {
    height: 65vh;
    overflow-y: scroll;
}

.todo_list::-webkit-scrollbar {
    display: none;
}

.todo_input {
    width: calc(100vw / 6);
    padding: 12px 24px;
    background-color: transparent;
    transition: transform 250ms ease-in-out;
    font-size: 14px;
    line-height: 18px;
    color: #4e6e41;
    background-position: 95% center;
    border-radius: 50px;
    border: 2px solid #4e6e41;
    transition: all 250ms ease-in-out;
    backface-visibility: hidden;
    transform-style: preserve-3d;
}

.todo_input:hover,
.todo_input:focus {
    padding: 12px 0;
    outline: 0;
    border: 2px solid transparent;
    border-bottom: 2px solid #4e6e41;
    border-radius: 0;
}



@media screen and (max-width: 599px) {
    #app {
        margin-left: 5vw;
        margin-right: 5vw;
    }
}

@media screen and (min-width: 600px) and (max-width: 899px) {
    #app {
        margin-left: 10vw;
        margin-right: 10vw;
    }
}

@media screen and (min-width: 900px) {
    #app {
        margin-left: 20vw;
        margin-right: 20vw;
    }
}

</style>
