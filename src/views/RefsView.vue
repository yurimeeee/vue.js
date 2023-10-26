<script>
  export default {
    data() {
    return {
      list: [
        'html', 'css', 'javascript'
      ]
    }
  },
    mounted() {
      //마운트 종료 후, 포커스
      //ref라고 별칭을 줌
      this.$refs.username.focus()
      //document.querySelector('#username').focus();
      console.log(this.$refs.items)
    }
  }
</script>


<template>
  <div class="layout">
    <h1>This is Template Refs page</h1>
    <input ref="username">
    <!-- <input type="text" id="username"> -->

    <ul>
      <li v-for="item in list" ref="items" :key="item.id">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
