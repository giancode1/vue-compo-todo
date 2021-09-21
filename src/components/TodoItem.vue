<template>
  <li class="list-group-item d-flex justify-content-between align-items-center">
      <span 
        role="button" 
        @click="changeCompleted(todo.id)"
        :class="{ 'text-decoration-line-through' : todo.completed==true }"
    >
          {{todo.task}}
      </span>

      <span role="button" @click="deleteTodo(todo.id)">
          <i class="fas fa-times"></i>
      </span>
  </li>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
    props: {
        todo:{
            type: Object,
            required: true
        }
    },
    setup(){
        const todos = inject('todos')

        const deleteTodo = (id) => {
            todos.value = todos.value.filter(item => item.id!==id )
        }
        const changeCompleted = (id) => {
            todos.value = todos.value.map(item => {
                if(item.id === id){
                    item.completed=!item.completed
                }
                return item
            }) 
        }
        return{
            deleteTodo,
            changeCompleted,
        }
    }
}
</script>

<style>

</style>