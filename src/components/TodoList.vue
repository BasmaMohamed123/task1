<template>
    <div class="todo-list">
      <h2 class="title">Todo List</h2>
      <form @submit.prevent="addTodo" class="todo-form">
        <div class="form-group">
          <label for="title">Title:</label>
          <input type="text" v-model="newTodo.title" placeholder="Enter task title" required />
        </div>
        <div class="form-group">
          <label for="description">Description:</label>
          <textarea v-model="newTodo.description" placeholder="Enter task description" required></textarea>
        </div>
        <div class="form-group">
          <label for="status">Status:</label>
          <select v-model="newTodo.status" required>
            <option value="pending">Pending</option>
            <option value="in-progress">In Progress</option>
            <option value="completed">Completed</option>
          </select>
        </div>
        <button type="submit" class="add-button">Add Todo</button>
      </form>
  
      <div class="todo-items">
        <div v-for="(todo, index) in todos" :key="index" class="todo-card">
          <h3 class="todo-title">{{ todo.title }}</h3>
          <p class="todo-description">{{ todo.description }}</p>
          <p class="todo-status">Status: <span :class="statusClass(todo.status)">{{ todo.status }}</span></p>
          <button @click="removeTodo(index)" class="remove-button">Remove</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTodo: {
          title: '',
          description: '',
          status: 'pending'
        },
        todos: []
      };
    },
    methods: {
      addTodo() {
        this.todos.push({ ...this.newTodo });
        this.newTodo.title = '';
        this.newTodo.description = '';
        this.newTodo.status = 'pending';
      },
      removeTodo(index) {
        this.todos.splice(index, 1);
      },
      statusClass(status) {
        return {
          'status-pending': status === 'pending',
          'status-in-progress': status === 'in-progress',
          'status-completed': status === 'completed'
        };
      }
    }
  };
  </script>
  
  <style scoped>
  .todo-list {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    padding: 20px;
    background-color: #f5f5f5;
  }
  
  .title {
    text-align: center;
    margin-bottom: 20px;
    color: #333;
  }
  
  .todo-form {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
    color: #555;
  }
  
  input[type="text"],
  textarea,
  select {
    width: 100%;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 14px;
    box-sizing: border-box;
  }
  
  .add-button {
    padding: 10px;
    background-color: #42b983;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.3s ease;
    align-self: center; /* Center align button */
  }
  
  .add-button:hover {
    background-color: #36a769;
  }
  
  .todo-items {
    display: flex;
    flex-direction: column;
    gap: 15px;
    max-width: 800px;
    margin: 0 auto;
  }
  
  .todo-card {
    background-color: #ffffff;
    padding: 15px;
    border: 1px solid #ddd;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .todo-title {
    margin: 0;
    color: #333;
  }
  
  .todo-description {
    margin: 10px 0;
    color: #666;
  }
  
  .todo-status {
    margin-bottom: 10px;
  }
  
  .status-pending {
    color: #e67e22;
  }
  
  .status-in-progress {
    color: #f39c12;
  }
  
  .status-completed {
    color: #2ecc71;
  }
  
  .remove-button {
    padding: 5px 10px;
    background-color: #e74c3c;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 14px;
  }
  
  .remove-button:hover {
    background-color: #c0392b;
  }
  
  /* Responsive adjustments */
  @media (max-width: 768px) {
    .todo-items {
      padding: 10px;
    }
  }
  </style>
  