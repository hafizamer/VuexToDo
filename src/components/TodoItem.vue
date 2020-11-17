<template>
    <div>
        <div class="row my-3 justify-content-between">

        <h3 v-if="!editing">{{todo.title}}</h3>
        <input v-bind:value ="todoText" 
        v-on:change="todoTextChange" 
        v-else 
        type="text" 
        class="col form-control" />
        <div>
            <button v-on:click="updateTodoI(todo)" class="btn btn-primary mx-2">{{editing?'Update':'Edit'}}</button>
            <button v-on:click="deleteTodo(todo.id)"  class="btn btn-danger">Delete</button>
        </div>
        </div>
    </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
    props:{
        todo:{}
    },
    methods: {
        ...mapActions(["deleteTodo", "updateTodo"]),
        todoTextChange(e){
            this.todoText=e.target.value;
        },
        updateTodoI(todo){
            this.editing =this.editing ==true ? false:true;
            if (this.editing){
                this.todoText=todo.title;
                this.updateTodo(todo);
            }else{
                todo.title=this.todoText;
            }
            
        }
    },
    data(){
        return{
            todoText:"",
            editing: false
        }
    },
}
</script>

<style scoped>

</style>