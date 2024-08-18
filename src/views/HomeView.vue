<template>
  <div class="home">
    <h1>Welcome to the Todo List App</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList.vue';

export default {
  name: 'HomeView',
  components: {
    TodoList
  }
};
</script>

<style scoped>
.home {
  background-image: url('../assets/home-background.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  min-height: 100vh;
  padding: 20px;
  text-align: center;
  color: #fff; 
}

h1 {
  font-size: 2.5em;
  margin-bottom: 20px;
  color: #166b31c5;
}
</style>
