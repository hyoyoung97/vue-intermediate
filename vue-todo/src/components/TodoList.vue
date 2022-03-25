<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in todoItems" :key="todoItem.item" class="shadow">
        <!--체크 아이콘-->
        <i class="checkBtn fa-solid fa-check" :class="{checkBtnCompleted: todoItem.completed}"
           @click="toggleComplete(todoItem)"></i>
        <span :class="{textCompleted: todoItem.completed}">{{ todoItem.item }}</span>
        <!--휴지통 아이콘-->
        <span class="removeBtn" @click="removeTodo((todoItem, index))">
          <i class="fa-solid fa-trash-can"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      todoItems: []
    }
  },
  created: function () {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        // this.todoItems[i] = localStorage.key(i);
        // this.todoItems.push(localStorage.key(i));
        console.log(JSON.parse(localStorage.getItem(localStorage.key(i))));
        this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
      }
    }
  },
  methods: {
    removeTodo: function (todoItem, index) {
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index, 1);  //splice - 특정 index에서 원하는 개수만큼 지울 수 있음, 기존 배열을 변경해서 새로운 배열을 만들어줌
    },
    toggleComplete: function (todoItem) {
      todoItem.completed = !todoItem.completed;
      // update 역할
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}

li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}

.removeBtn {
  margin-left: auto;
  color: #de4343;
}

.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}

.checkBtnCompleted {
  color: #b3adad;
}

.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}

</style>