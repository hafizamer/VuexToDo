<template>
    <div>
        <div class="row">
        <input v-on:change="todoTextChange" v-bind:value="todoText" class="col form-control mx-2" type="text" />
        <button v-on:click="addTodoI" class="btn btn-primary">Add</button>
        </div>
    </div>
</template>

<script>
import{ mapActions } from 'vuex';
import { v1 } from 'uuid';
export default {
    data(){
        return{
            todoText:""
        }
    },
   methods:{
       ...mapActions(["addTodo"]),
       todoTextChange(e){
           this.todoText=e.target.value;//based on the textbox
       },
       addTodoI(){
          this.addTodo({
              id: v1(),
              title: this.todoText
          });
          this.todoText=""; 
       }
   } 
}
</script>

<style scoped>

</style>