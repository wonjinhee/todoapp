<template>
  <div>
    <ul class="todo_list">
      <li v-for="todoItem in todoItems" v-bind:key="todoItem">{{ todoItem }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function(){
    todoItems: []
  },
  created: function(){
    console.log(localStorage.length);
    if(localStorage.length > 0){
      for (let i = 0; i < localStorage.length; i++) {
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          this.todoItems.push(localStorage.key(i));
        }
      }
    }
  }
}
</script>

<style>

</style>
