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
      this.getTodoListCheckedLength()
	  },

    // 更新每个代办项的状态
    changeCheck(id){
      this.todoList.forEach(element => {
        if(element.id == id) return element.done = !element.done
      });
      this.getTodoListCheckedLength()
    },

    // 删除某一项todo
    deleteTodo(id) {
      this.todoList = this.todoList.filter( e => e.id != id )
      this.getTodoListLength()
      this.getTodoListCheckedLength()
    },

    // 用于统计列表长度
    getTodoListLength(){
      this.$bus.$emit('getTodoListLength',this.todoList.length)
    },

    // 用于获取列表中已经选中的事件数
    getTodoListCheckedLength(){
      this.$bus.$emit('getTodoListCheckedLength',this.todoListCheckedLength)
    }
  },
  components: {
    MyList, MyHeader, MyFooter
  },
  mounted() {
    // 更新每个事件的选中状态
    this.$bus.$on('changeCheck',this.changeCheck)
    // 删除某一项todo
    this.$bus.$on('deleteTodo',this.deleteTodo)
    // 获取todoList长度，将长度给子组件
    this.getTodoListLength()
    // 获取列表中已经选中的事件数，将事件数传递给子组件
    this.getTodoListCheckedLength()
  },
  computed: {
    todoListCheckedLength(){
      return this.todoList.reduce( (pre,current) => {
        return pre + (current.done ? 1 : 0)
      },0)
    }
  }
}
</script>

<style scoped>

</style>
