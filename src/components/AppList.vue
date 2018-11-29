<template>
  <div>
    <ul class="todo_list">
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" v-bind:class="{complete_item:todoItem.completed}">
        <div class="chk_icon" v-on:click="btnChkComplete(todoItem, index)"><i class="fas fa-check" v-if="todoItem.completed"></i></div>
        <div class="todo_txt">{{ todoItem.item }}</div>
        <button class="btn_del" v-on:click="removeItem(todoItem, index)"><i class="far fa-trash-alt"></i></button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props:["propsdata"],
  methods:{
    removeItem: function(todoItem, index){
      this.$emit("removeListItem", todoItem, index);
    },
    btnChkComplete: function(todoItem, index){
      todoItem.completed = !todoItem.completed;
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem))
    }
  }
}
</script>

<style>
ul, li{margin:0; padding:0; list-style: none;}
.todo_list li{position:relative; display:block; margin:2px 0; border:#ededed solid 1px; padding:8px 30px 8px 40px; color:#999; }
.todo_txt{color:#232323}
.chk_icon{position: absolute; left:8px; top:8px; width:22px; height:22px; text-align:center; line-height:22px; border:#999 solid 1px; border-radius:50%; font-size:12px; }
.btn_del{position:absolute; right:0; top:0; padding:8px; border:none; background: transparent }
.complete_item{ opacity: 0.5;}
.complete_item .todo_txt{}
</style>
