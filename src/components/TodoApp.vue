<template>
  <todo-form /> 
  <todo-list />
</template>

<script>
import { ref } from '@vue/reactivity'
import TodoForm from './TodoForm.vue'
import { provide, watchEffect } from '@vue/runtime-core'
import TodoList from './TodoList.vue'

export default {
    components: { TodoForm, TodoList },

    setup() {
        const todos = ref([])
        provide('todos', todos)

        if(localStorage.getItem('todos')){
          todos.value = JSON.parse(localStorage.getItem('todos'))
        }
        
        watchEffect(()=>{
          //console.log(todos.value)
          localStorage.setItem('todos', JSON.stringify(todos.value))
        })

    }
}
</script>

<style>

</style>