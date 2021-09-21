<template>
  <div class="card mt-2 mb-3 ">
      <div class="card-body d-flex justify-content-between align-items-center">
          <span @click=" selection = 'active' "   :class="{'text-primary' : selection==='active'}"   role="button">Active</span>
          <span @click=" selection = 'all' "      :class="{'text-primary' : selection==='all'}"      role="button">All</span>
          <span @click=" selection = 'complete' " :class="{'text-primary' : selection==='complete'}" role="button">Complete</span>
      </div>
  </div>
</template>

<script>
import { inject, watchEffect } from '@vue/runtime-core'
export default {

    setup(){
        const selection = inject('selection')

        watchEffect(()=>{
            console.log('selection.value',selection.value)

        })

        return{
            selection
        }
    }
}
</script>

<style>

</style>