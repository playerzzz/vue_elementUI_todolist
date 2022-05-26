<template>
  <div>
    <el-table :data="todos" style="width: 50%" row-key="id">
      <el-table-column label="计划" width="580">
        <template scope="scope">
          <div>
            <el-checkbox 
              class="checkText"
              :checked="scope.row.done" 
              @change="changeItemCheck(scope.row.id)">{{scope.row.title}}
            </el-checkbox>
          </div>
        </template>
      </el-table-column>
      <el-table-column label="操作" width="180">
        <el-button type="danger" size="mini">删除</el-button>
      </el-table-column>
    </el-table>
  </div>
</template>
<script>
export default {
  data() {
    return {

    }
  },
  props: ['todos','changeCheck'],
  methods: {
    // 当选择的状态发生变化时触发的函数
    changeItemCheck(id){
      this.changeCheck(id)
    }
  },
}
</script>
<style lang="less" scoped>
.el-table {
  margin: 0 auto;
  margin-top: 15px;
}

.el-table /deep/ th.el-table__cell > .cell {
  padding-left: 4px;
  height: 39px;
  font-size: 31px;
  line-height: 44px;
}
.el-table::before {
  height: 0px;
}

// 关闭表格中添加的动画效果
.el-table--enable-row-transition /deep/ .el-table__body td.el-table__cell {
  transition:none !important
}



/deep/ .el-checkbox__label {
  .checkText
}

.checkText  {
  text-decoration: line-through !important;
}
</style>