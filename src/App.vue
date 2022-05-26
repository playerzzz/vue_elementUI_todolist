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
      this.getTodoListLength()
	  },

    // 更新每个代办项的状态
    changeCheck(id){
      this.todoList.forEach(element => {
        if(element.id == id) return element.done = !element.done
      });
    },

    // 删除某一项todo
    deleteTodo(id) {
      this.todoList = this.todoList.filter( e => e.id != id )
      this.getTodoListLength()
    },

    // 用于统计列表长度
    getTodoListLength(){
      console.log(this.todoList.length);
      this.$bus.$emit('getTodoListLength',this.todoList.length)
    }
  },
  components: {
    MyList, MyHeader, MyFooter
  },
  created() {
    this.getTodoListLength()
  },
  mounted() {
    // 更新每个事件的选中状态
    this.$bus.$on('changeCheck',this.changeCheck)
    // 删除某一项todo
    this.$bus.$on('deleteTodo',this.deleteTodo)
    
  },
  computed: {

  }
}
</script>

<style scoped>

</style>
