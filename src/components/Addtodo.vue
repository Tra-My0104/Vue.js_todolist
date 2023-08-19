<template>
  <div class="form-todo">
    <form @submit="addTodo">
      <label
        style="
          display: block;
          margin-bottom: 0px;
          font-size: larger;
          text-align: center;
          font-weight: 500;
        "
        >Nhập công việc</label
      >
      <br />
      <input type="text" placeholder="công việc mới" v-model="tilte"/>
      <button type="submit" @click="handleAdd" class="add">Thêm</button>
    </form>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: "Addtodo",
  setup (props , context) {
    const tilte = ref("");
    const addTodo = event => {
      event.preventDefault();
      const newTodo = {
        id : Math.random()*100,
        tilte : tilte.value,
        complted : false
      }

      context.emit('add' , newTodo)
      tilte.value = ""
    }

    return { tilte , addTodo}
  }
};
</script>

<style scoped>
.form-todo {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 10px;
}

input {
  height: 30px;
  width: 300px;
  margin-right: 20px;
}
.add {
  background-color: rgb(80, 138, 245);
  color: white;
  height: 40px;
  width: 100px;
  border: none;
  border-radius: 5px;
}
</style>
