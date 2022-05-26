<template>
  <div>
    <div class="divBox" style="width: 50%">
      <el-checkbox>已完成0 / 全部{{total}}</el-checkbox>
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
      console.log('footer' + length);
      this.total = length
    }
  },
  mounted() {
    this.$bus.$on('getTodoListLength',this.getTodoListLength)
  },
  computed:{
    // total
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