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

        // watchEffect(()=>{
        //     console.log(todos.value.length)
        //     console.log(todos.value)
        // })

        console.log('me genere TodoApp')
        return{

        }
    }
}
</script>

<style>

</style>