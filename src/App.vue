<template>
  <div id="app">
    <app-header></app-header>
    <app-input v-on:addInputItem="addTodoItem"></app-input>
    <app-list v-bind:propsdata="todoItems" v-on:removeListItem="removeItem"></app-list>
    <app-footer v-on:clearAll="clearAllTodo"></app-footer>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader';
import AppInput from './components/AppInput';
import AppList from './components/AppList';
import AppFooter from './components/AppFooter';

export default {
  name: 'app',
  data: function(){
    return{
      todoItems: []
    }
  },
  methods:{
    addTodoItem: function(todoItem){
      var obj = {completed:false, item:todoItem}
      localStorage.setItem(todoItem, JSON.stringify(obj));
      this.todoItems.push(obj)
    },
    removeItem: function(todoItem, index){
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index,1);
    },
    clearAllTodo: function(){
      localStorage.clear();
      this.todoItems = [];
    }
  },
  created: function(){
    console.log("length ",localStorage.length);
    if(localStorage.length > 0){
      for (let i = 0; i < localStorage.length; i++) {
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
        }
      }
    }
  },
  components:{
    'app-header':AppHeader,
    'app-input':AppInput,
    'app-list':AppList,
    'app-footer':AppFooter
  }
}
</script>

<style>
* {box-sizing: border-box;}
</style>
