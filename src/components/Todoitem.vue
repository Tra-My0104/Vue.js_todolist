<template>
  <div :class="['list-item', propTodo.complted ? 'check' : '']">
  <input type="checkbox"  :checked="propTodo.complted" v-on:change="handleCheck">
  {{ propTodo.tilte }}
  <button class="deleteBtn" @click="handleDelete">Delete</button>
</div>
</template>

<script>
import { ref } from 'vue'

export default {
  name : "Todoitem",
  props : ['propTodo'],
  setup (props , context) {
    // setup luôn chứa 
    //prop : để truyền từ component cha xuống
    // context : là những thứ khác
    const handleCheck = () => {
      // console.log(props.propTodo)
      context.emit('list-item' , props.propTodo.id) // gửi tín hiệu từ component con lên component cha 
      //("hành động từ component con" , data)
    }

    const handleDelete = () => {
      // console.log('id')
      context.emit('deleteBtn' , props.propTodo.id)
    }

    return {
      handleCheck,
      handleDelete
    }
  }
}
</script>

<style>
  .deleteBtn {
    background-color: red;
    color: rgb(255, 255, 255);
    border: none;
    border-radius: 5px;
    cursor: pointer;
    float: right;
  }

  .list-item{
    background-color: rgb(224, 224, 224);
    margin: 0;
    padding: 5px;
    border-bottom: 1px gray dotted;
  }

  .check{
    text-decoration-line: line-through;
  }
</style>