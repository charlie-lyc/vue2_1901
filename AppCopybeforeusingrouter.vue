<template>
    <div id="app">
  
      <!-- <HelloWorld msg="Welocome to VueJS!"/> -->
  
      <!-- {{ message }} -->
  
      <Header />
  
      <AddTodo 
        v-on:add-todo="handleAddTodo" 
      />
  
      <TodoList 
        v-bind:todos="todos"
        v-on:toggle-complete="handleToggleComplete" 
        v-on:delete-todo="handleDeleteTodo" 
      /> 
  
    </div>
  </template>
  
  <script>
    // import HelloWorld from './components/HelloWorld.vue'
    import TodoList from './components/TodoList.vue'
    import Header from './components/layout/Header.vue'
    import AddTodo from './components/AddTodo.vue'
  
    export default {
      name: 'App', // 오직 유일하게 single word!!!
      components: {
        // HelloWorld,
        Header,
        AddTodo,
        TodoList,
      },
      methods: {
        handleToggleComplete(id) {
          // console.log('toggle event completed', todoId)
          const todoItem = this.todos.find((item) => item.id === id)
          if (todoItem) {
            todoItem.completed = !todoItem.completed
          }
        },
        handleDeleteTodo(id) {
          /* In Memory */
          // this.todos = this.todos.filter((item) => item.id !== id)
          ///////////////////////////////////////////////////////////
          /* JSON Placeholder API */
          fetch(`https://jsonplaceholder.typicode.com/todos/${id}`, {
              method: 'DELETE',
            }).then((response) => response.json())
            .then((data) => {
              // console.log(data)
              if (data) {
                // console.log(`deleted item: ${id}`)
                this.todos = this.todos.filter((item) => item.id !== id)
              }
            }).catch((err) => console.log(err))
  
        },
        handleAddTodo(title) {
          /* In Memory */
          // const newId = this.todos.length + 2
          // this.todos.push({
          //   id: newId,
          //   title: title,
          //   completed: false
          // })
          //////////////////////////////////////////////////////
          /* JSON Placeholder API */
          fetch('https://jsonplaceholder.typicode.com/todos', {
              method: 'POST',
              body: JSON.stringify({
                title: title,
                completed: false
              }),
              headers: { 
                'Content-type': 'application/json; charset=UTF-8',
              },
            }).then((response) => response.json())
            .then((data) => {
              // console.log(data)
              this.todos.push(data)
            }).catch((err) => console.log(err))
        },
      },
      data() {
        return {
          // message: 'Hello',
          /////////////////////////
          /* In Memory */
          // todos: [
          //   {
          //     id: 1,
          //     title: 'Item One',
          //     completed: false
          //   },
          //   {
          //     id: 2,
          //     title: 'Item Two',
          //     completed: true
          //   },
          //   {
          //     id: 3,
          //     title: 'Item Three',
          //     completed: false
          //   },
          // ],
          /////////////////////////
          /* JSON Placeholder API */
          todos: []
        }
      },
      created() {
        fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
          .then(response => response.json())
          .then(data => {
            // console.log(data)
            this.todos = data
          }).catch((err) => console.log(err))
      }
  
    }
  </script>
  
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: Arial, Helvetica, sans-serif;
      line-height: 1.4;
    }
  
    .btn {
      display: inline-block;
      border: none;
      background: #555;
      color: #fff;
      padding: 7px 20px;
      cursor: pointer;
    }
    .btn:hover {
      background: #666;
    }
  </style>
  