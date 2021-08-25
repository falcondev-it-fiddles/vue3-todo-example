<template>
  <List :todos="todos" />
  <div>
    <input type="text" placeholder="neues Todo" v-model="newTodoText" />
    <input type="button" value="Adden" @click="addTodo" />
  </div>
</template>

<script>
import { ref } from "vue"
import List from "./components/List.vue"

export default {
  components: { List },
  setup() {
    const todos = ref(JSON.parse(localStorage.getItem("todoList")) ?? [])
    const newTodoText = ref()

    const addTodo = () => {
      todos.value.push(newTodoText.value)
      localStorage.setItem("todoList", JSON.stringify(todos.value))
      newTodoText.value = ""
    }

    return { todos, addTodo, newTodoText }
  },
}
</script>
