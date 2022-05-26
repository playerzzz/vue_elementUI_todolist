<template>
  <div>
    <!-- 输入框 -->
    <el-input v-model="todoText" placeholder="请输入任务，按回车键确认" @change="sendTodoItem"></el-input>
  </div>
</template>
<script>
import {nanoid} from 'nanoid'
export default {
  data() {
    return {
      todoText: ''
    }
  },
  props: ['changeTodoList'],
  methods: {
    sendTodoItem() {
      let obj = {id:nanoid(),title:this.todoText,done:false}
      console.log(obj);
      this.changeTodoList(obj)
      this.todoText = ''
    }
  },
}
</script>
<style lang="less" scoped>
.el-input {
  width: 29%;
  margin-left: 378px;
}
</style>