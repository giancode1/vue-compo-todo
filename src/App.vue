<template>
  <div class="container">
      <h1>ToDos</h1>
      <todo-app />
  </div>
</template>

<script>
import TodoApp from './components/TodoApp.vue'


export default {
  name: 'App',
  components: {
    TodoApp
    
  }
}
</script>

<style>

</style>
