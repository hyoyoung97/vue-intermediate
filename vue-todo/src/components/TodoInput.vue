<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" @keyup.enter="addTodo">
    <!--<button @click="addTodo">add</button>-->
    <span class="addContainer" @click="addTodo">
      <i class="fa-solid fa-plus addBtn"></i>
    </span>
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
      if (this.newTodoItem !== '') {
        var obj = {completed: false, item: this.newTodoItem};
        //js 객체를 string으로 변환해주는 값
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));  // Value > {completed: false, item: this.newTodoItem}
        // localStorage.setItem(this.newTodoItem, obj); // Value > [object Object]
        // localStorage.setItem(this.newTodoItem, this.newTodoItem); //개발자도구-애플리케이션에서 확인 가능함
        this.clearInput();
      }
    },
    clearInput: function () {
      this.newTodoItem = '';
    }
  }
}
</script>

<style scoped>
input:focus {
  outline: none;
}

.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}

.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}

.addContainer {
  float: right;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}

.addBtn {
  color: white;
  vertical-align: middle;
}
</style>