<template>
  <div>
    <el-form :inline="true" :model="formInline" class="demo-form-inline">
      <el-form-item>
        <el-button type="primary" @click="dialogFormVisible = true">添加时间段</el-button>
      </el-form-item>
    </el-form>
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="Name" label="名称" width="180"></el-table-column>
      <el-table-column prop="Visits" label="时间段"></el-table-column>
      <el-table-column label="操作" width="240">
        <template scope="scope" width="240">
          <el-button size="mini" @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
          <el-button size="mini" type="danger" @click="handleDelete(scope.$index, scope.row)">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
  
    <el-dialog title="添加时间段" :visible.sync="dialogFormVisible">
      <el-form :model="form">
        <el-form-item label="时间段" :label-width="formLabelWidth">
          <el-input v-model="form.name" auto-complete="off"></el-input>
        </el-form-item>
        <el-form-item label="时间范围" :label-width="formLabelWidth">
          <el-time-picker
            is-range
            v-model="timeRange"
            placeholder="选择时间范围">
          </el-time-picker>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
      </div>
    </el-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tableData: [{
        Name: '全天',
        Visits: '00:00 - 24:00'
      }, {
        Name: '早餐',
        Visits: '08:00 - 10:00'
      }, {
        Name: '午餐',
        Visits: '11:00 - 14:00'
      }, {
        Name: '晚餐',
        Visits: '17:00 - 23:00'
      }],
      dialogFormVisible: false,
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      },
      formLabelWidth: '120px',      
      timeRange: [new Date(2016, 9, 10, 8, 40), new Date(2016, 9, 10, 9, 40)]
    }
  }
}
</script>
<style scoped>

</style>
