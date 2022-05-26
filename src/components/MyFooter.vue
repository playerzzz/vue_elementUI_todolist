<template>
  <div>
    <div class="divBox" style="width: 50%">
      <el-checkbox @change="changeCheck">已完成{{haveDone}} / 全部{{total}}</el-checkbox>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      haveDone:0,
      total:1
    }
  },
  methods: {
    getTodoListLength(length) {
      this.total = length
    },

    getTodoListCheckedLength(length){
      console.log(length);
      this.haveDone = length
    },

    // 底部全选按钮的切换
    changeCheck(value){
      console.log(value);
    }
  },
  mounted() {
    this.$bus.$on('getTodoListLength',this.getTodoListLength)
    this.$bus.$on('getTodoListCheckedLength',this.getTodoListCheckedLength)
  },
  computed:{
  }
}
</script>
<style lang="less" scoped>
.divBox {
  border: 1px solid #ebeef5;
  box-sizing: border-box;
  height: 50px;
  margin: 0 auto;
  margin-top: 15px;
  line-height: 50px;
  padding-left: 12px;
}
</style>