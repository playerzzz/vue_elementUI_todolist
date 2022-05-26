<template>
  <div>
    <el-table :data="todos" style="width: 50%" row-key="id"  >
      <el-table-column label="计划" width="580">
        <template scope="scope">
          <div>
            <el-checkbox v-model="scope.row.done" @change="changeItemCheck(scope.row.id)">
              <div class="checkText" v-if="scope.row.done">
                {{scope.row.title}}
              </div>
              <div v-else>
                {{scope.row.title }}
              </div>
            </el-checkbox>
          </div>
        </template>
      </el-table-column>
      <el-table-column label="操作" width="180">
        <template scope="scope">
          <el-button class="deleteButton" type="danger" @click="deleteTodo(scope.row.id)" size="mini">删除</el-button>
        </template>
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
  props: ['todos', 'changeCheck'],
  methods: {
    // 当选择的状态发生变化时触发的函数
    changeItemCheck(id) {
      this.$bus.$emit('changeCheck', id)
    },

    // 删除某一项todo
    deleteTodo(id) {
      this.$bus.$emit('deleteTodo',id)
    }
  },
  computed: {
    textStyle() {
      return
    }
  }
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
  transition: none !important;
}

.checkText {
  text-decoration: line-through;
}

.deleteButton {
  display: none;
}
/deep/ .el-table__row {
  height: 53px !important;
}
.el-table__row:hover .deleteButton{
  display: block;
}

</style>