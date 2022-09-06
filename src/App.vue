<script>
  let id = 0

  export default {
    data() {
    return {
      newTodo: '',
      todos: [
        { id: id++, text: 'Add text' }        
      ]
    }
  },
  methods: {
    addTodo() {
      this.todos.push({ id: id++, text: this.newTodo })
      this.newTodo = ''
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((t) => t !== todo)
    }
  }
}
</script>

<template>
  <div class="container">
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" class="newTodo">
      <button class="addBtn">Add a new task</button>    
    </form>
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
      <button @click="removeTodo(todo)">X</button>
      </li>
    </ul>
  </div>
  
</template>
  
<style>
  .container {
    width: 800px;
    margin: 0 auto;
    padding: 0 15px;
  }

  .newTodo {
    width: calc(100% - 150px);
    height: 40px;
    text-indent: 10px;
    border: 1px solid rgb(0, 0, 0);
    border-radius: 5px;
    border-radius: 0;
    box-sizing: border-box;
    outline: none;
    transition: 0.2s border;
  }

  .addBtn {
    background-color: #12c0dd;
    border: 1px solid #12c0dd;
    color: #fff;
    font-weight: 700;
    text-transform: uppercase;
    padding: 10px 15px;
    font-size: 12px;
    height: 40px;
    outline: none;
    transition: 0.2s;
  }

  .addBtn:hover {
    background-color: #0dd6f8;
    border-color: #0dd6f8;
  }

  form {
    width: 90%;
    display: flex;
    justify-content: space-between;
  }
</style>
