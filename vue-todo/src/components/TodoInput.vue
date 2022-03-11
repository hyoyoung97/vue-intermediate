<template>
  <div>
    <input type="text" v-model="newTodoItem">
    <button @click="addTodo">add</button>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      newTodoItem: ""
    }
  },
  methods: {
    addTodo: function () {
      localStorage.setItem(this.newTodoItem, this.newTodoItem); //개발자도구-애플리케이션에서 확인 가능함
      this.newTodoItem = '';
    }
  }
}
</script>

<style scoped>

</style>