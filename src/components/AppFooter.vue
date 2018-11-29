<template>
  <div>
    <div class="text-center">
      <button class="btn_clearall" v-on:click="clearAllItem">Clear All</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    clearAllItem: function(){
      this.$emit("clearAll")
    }
  }
}
</script>

<style scoped>
.text-center{text-align:center; margin-top:10px;}
.btn_clearall{display:inline-block; padding:10px 20px; color:#ff0000; border:#ccc solid 1px; background:#fff; }
</style>
