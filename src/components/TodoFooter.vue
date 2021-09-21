<template>
    <li class="list-group-item d-flex justify-content-between align-items-center">
      <span 
        role="button" 
    >
          {{todosIncomplete}} Incompletos
      </span>

      <span role="button" @click="deleteCompleted()">
          Eliminar Completados
      </span>
  </li>
</template>

<script>
import { computed, inject } from '@vue/runtime-core'
export default {

  setup(){
    const todos = inject('todos')
    
    const todosIncomplete = computed(()=>{
      return todos.value.filter(item => item.completed === false).length
    })

    const deleteCompleted = () => {
      todos.value = todos.value.filter(item => item.completed===false)
    }


    return {
      todos,
      todosIncomplete,
      deleteCompleted
    }
  }
}
</script>

<style>

</style>