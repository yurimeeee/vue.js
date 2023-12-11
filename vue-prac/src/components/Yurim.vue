<template>
  <h2>{{ mss }}</h2>
  <p v-if="seen">이제 나를 볼 수 있어요</p>
  <ol>
    <li v-for="todo in todos" :key="todo.text" :id="todo.text">
      {{ todo.text }}
    </li>
  </ol>
</template>

<script>
export default {
  name: 'YurimHappy',
  props: {
    mss: String
  },
  data: function () {
    return {
      seen: true,
      todos: [
        { text: 'JavaScript 배우기' },
        { text: 'Vue 배우기' },
        { text: '무언가 멋진 것을 만들기' }
      ]
    };
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
