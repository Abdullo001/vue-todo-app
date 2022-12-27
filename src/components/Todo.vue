<template lang="">
  <li class="d-flex todo-box">
    <div>
      <input type="checkbox" class="me-1  " v-model="todos.isComplate">
      <strong 
      class="todo-name"
       @click="onLike">
       {{this.todos.name}}
      </strong>
    </div> 
    <div class="button-group">
      <button class="btn btn-danger"  >
        delete
      </button>
    </div>
  </li>
</template>

<script>
export default {
  props:{
    todos:{
      type:Object,
      required:true,
    }
  },

  methods: {
    onLike(){
       this.$emit('onLike',this.todos.id)  
    }


  },
}
</script>

<style >
  .todo-name{
    display: inline-block;
  }
  .todo-box{
    justify-content: space-between;
  }
  .isChecked{
    text-decoration: line-through;
  }
</style>