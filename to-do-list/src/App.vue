<script>
import Todo from './components/Todo.vue';

export default {
  components: {
    Todo
  },
  data() {
    return {
      todoText: '',
      todos: [
        { id: 1, text: 'Learn Vue.js', checked: false },
        { id: 2, text: 'Get a job', checked: false },
      ]
    }
  },
  methods: {
    AddTodo(e) {
      // console.log(e.target.value)
      this.todos.push({//본 export default 안의 것들을 this로 받음
        id: Math.random(),
        text: e.target.value,
        checked: false
      });
      this.todoText = '';
    },
    toggleCheck({ id, checked }) { //일치하는 것의 첫번째
      const index = this.todos.findIndex(todo => todo.id === id);
      this.todos[index].checked = checked;
      console.log(this.todos);
    },
    deleteTodo() {

    }
  }
}

</script>

<template>
  <div class="container">
    <h1 class="text-center">To Do List</h1>
    <div class="mb-3">
      <label for="todo" class="form-label">To do</label>
      <input type="text" class="form-control" id="todo" placeholder="할일을 입력하세요" required @keyup.enter="AddTodo"
        v-model="todoText">
    </div>
    <!-- <Todo v-for="todo in todos" :key="todo.id" :todo="todo" @toggle-checkbox="toggleCheck" /> -->
    <Todo v-for="todo in todos" :key="todo.id" :todo="todo" @toggle-checkbox="toggleCheck" @click-delete="deleteTodo" />
  </div>
</template>

<style scoped></style>