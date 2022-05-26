<template>
  <div id="app">
    <MyHeader :changeTodoList="changeTodoList"></MyHeader>
    <MyList :todos="todoList" :changeCheck="changeCheck"></MyList>
    <MyFooter></MyFooter>
  </div>
</template>

<script>
import MyList from './components/MyList.vue'
import MyHeader from './components/MyHeader.vue'
import MyFooter from './components/MyFooter.vue'

export default {
  name: 'App',
  data() {
    return {
      todoList: [
        { id: '001', title: '吃饭', done: true },
        { id: '002', title: '睡觉', done: false },
        { id: '003', title: '玩游戏', done: true }
      ],
    }
  },
  methods: {
    // 添加计划做的事
	  changeTodoList(todoItem){
		  this.todoList.unshift(todoItem)
	  },

    // 更新每个代办项的状态
    changeCheck(id){
      console.log(id);
    }


  },
  components: {
    MyList, MyHeader, MyFooter
  }
}
</script>

<style scoped>

</style>
