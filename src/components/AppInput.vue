<template>
  <div>
    <div class="input_wrap">
      <input type="text" class="form_control" placeholder="할 일을 입력해주세요" v-model="newTodoItem" v-on:keyup.enter="addTodo"/>
      <span class="btn_add" v-on:click="addTodo">
        <i class="fas fa-plus"></i>
      </span>
    </div>
  </div>
</template>

<script>

export default {
  data: function(){
    return{
      newTodoItem:""
    }
  },
  methods:{
    addTodo: function(){
      localStorage.setItem(this.newTodoItem, this.newTodoItem);
      this.clearInput();
    },
    clearInput: function(){
      this.newTodoItem = "";
    }
  }
}
</script>

<style scoped>
  .input_wrap{display:table; width:100%;  }
  .input_wrap .form_control{display:table-cell; width:100%; padding:0 10px;  border:#ccc solid 1px; border-right:none; height:40px;}
  .btn_add{display:table-cell; background:rgb(44, 171, 255); color:#fff; font-size:24px; width:40px; text-align: center; vertical-align: middle }
</style>
