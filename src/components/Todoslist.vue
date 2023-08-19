<template>
  <div>
    <Addtodo @add = "addTodo"/>
    <Todoitem
      v-for="todo in todos"
      v-bind:key="todo.id"
      v-bind:propTodo="todo"
      v-on:list-item="handleCheck"
      @deleteBtn="handleDelete"
    />
  </div>
</template>

<script>
import { ref } from "vue";
import Todoitem from "./Todoitem.vue";
import Addtodo from "./Addtodo.vue";

export default {
  name: "Todolist",
  components: { Todoitem , Addtodo},
  setup() {
    const todos = ref([
      {
        id: 1,
        tilte: "Việc thứ nhất",
        complted: true,
      },
      {
        id: 2,
        tilte: "Việc thứ hai",
        complted: false,
      },
      {
        id: 3,
        tilte: "Việc thứ ba",
        complted: false,
      },
    ]);

    const handleCheck = (id) => {
      todos.value = todos.value.map((todo) => {
        if (todo.id === id) {
          todo.complted = !todo.complted; // Đảo ngược completed
        }
        return todo;
      });
    };

    const handleDelete = (id) => {
      console.log(id)
      todos.value = todos.value.filter(todo => todo.id !== id)
    }

    const addTodo = newTodo => {
      console.log(newTodo.id)
      todos.value.push(newTodo)
    }
    return { todos, handleCheck , handleDelete , addTodo};
  },
};
</script>

<style></style>
