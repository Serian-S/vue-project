<template>
  <div class="todo-app">
    <div class="title">申佳洁的todo app</div>
    <div class="todo-from">
      <input v-model="str" class="todo-input" type="text" placeholder="add a todo" />
      <div @click="add" class="todo-button">add todo</div>
    </div>

    <div v-for="(item,index) in list" 
    :class="[item.iscomplete?'completed':'item']">
      <div>
        <input v-model="item.iscomplete" type="checkbox" />
        <span class="name">{{ item.text }}</span>
      </div>
      <div @click="del(index)" class="del">del</div>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue';

const str = ref('')
const list = ref(
  [
    {
      iscomplete:false,
      text:'吃饭',
    },
  ]
)
function add() {
  list.value.push({
      iscomplete:false,
      text:str.value
  })
  str.value=''
}
function del(index) {
  list.value.splice(index,1)
}

</script>

<!-- 这里是你要恢复的样式 -->
<style scoped>
/* 所有你写在 HTML 里的样式，全部搬到这里，只加 scoped */
.completed {
  text-decoration: line-through;
  opacity: 0.4;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-sizing: border-box;
  width: 80%;
  height: 50px;
  margin: 8px auto;
  padding: 16px;
  border-radius: 20px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
}
.del {
  color: red;
}
.item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-sizing: border-box;
  width: 80%;
  height: 50px;
  margin: 8px auto;
  padding: 16px;
  border-radius: 20px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
}
.todo-button {
  width: 100px;
  height: 50px;
  border-radius: 0 20px 20px 0;
  text-align: center;
  line-height: 50px;
  background: linear-gradient(
    to right,
    rgb(113, 65, 168),
    rgba(44, 114, 251, 1)
  );
  color: #ffff;
  cursor: pointer;
  user-select: none;
}
.todo-input {
  margin-bottom: 20px;
  border: 1px solid #dfe1e5;
  outline: none;
  width: 60%;
  height: 50px;
  border-radius: 20px 0 0 20px;
  padding-left: 15px;
}
.todo-from {
  display: flex;
  margin-top: 20px;
  margin-left: 30px;
}
.todo-app {
  padding-top: 30px;
  box-sizing: border-box;
  width: 98%;          
  height: 500px;
  background-color: #ffff;
  border-radius: 5px;
  margin-top: 40px;     
  margin-left: 1%;     
}
.title {
  font-size: 30px;
  font-weight: 700;
  text-align: center;
}
</style>

<style>
body {
  background: linear-gradient(
    to right,
    rgb(113, 65, 168),
    rgba(44, 114, 251, 1)
  );
  margin: 0;
  min-height: 100vh;
}
</style>