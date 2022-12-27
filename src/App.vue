<template>
  <div>
    <div class="container">
      <h1 class="text-center">Hello world</h1>
      <div class="inner w-50 mx-auto" >
        <form class="d-flex mb-5" @submit.prevent>
          <input
            type="text"
            class="form-control input-value me-2"
            v-bind:value="name"
            @input="name = $event.target.value"
            
          />
          <button class="btn btn-success" @click="handlerSubmitTodos">Submit</button>
        </form>

        <ul class="list-unstyled">
          <Todo class="todo" v-for="todo in todos" v-bind:todos="todo" @onLike="onLikeHandler" v-bind:key="todo.id"/> 
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./components/Todo.vue"
export default {

  components:{
    Todo
  },
  
  data() {
    return {
      todos:  JSON.parse(window.localStorage.getItem("Todos"))||[],

      name: "",
    };
  },

  methods: {
    handlerSubmitTodos() {
      const newTodo = {
        id: this.todos.length+1,
        name: this.name,
        isComplate: false,
      };

      console.log(newTodo);
      this.todos.unshift(newTodo);

      this.name="";
      window.localStorage.setItem("Todos",JSON.stringify(this.todos))
    },

    onLikeHandler(id){
      const arr=this.todos.map(item=>{
        if(item.id==id){
          item.isComplate=!item.isComplate
          console.log(item);
        }
        window.localStorage.setItem("Todos",JSON.stringify(this.todos))
      })
      
    }
  },
};
</script>

<style >
</style>