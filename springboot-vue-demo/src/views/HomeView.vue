<template>
  <div class="home" style="width: 100%;padding: 10px">
    <div style="margin:10px 0;">
      <el-button type="primary">新增</el-button>
      <el-button type="primary">导入</el-button>
      <el-button type="primary">导出</el-button>
      <el-input v-model="search" placeholder="请输入内容" style="width:20%;margin-left:10px;"></el-input>
      <el-button type="primary" style="margin-left:10px;">查询</el-button>
    </div>
    <el-table :data="tableData" border stripe style="width: 100%;">
      <el-table-column prop="date" label="日期" width="180" sortable />
      <el-table-column prop="name" label="姓名" width="180" />
      <el-table-column prop="address" label="地址" />
      <el-table-column fixed="right" label="操作" width="140">
        <template #default="scope">
          <el-button type="text" size="small" @click="handleEdit(scope.row)">编辑</el-button>
          <el-popconfirm title="Are you sure to delete this?">
            <template #reference>
              <el-button type="text" size="small">删除</el-button>
            </template>
          </el-popconfirm>
        </template>
      </el-table-column>
    </el-table>
    <div style="margin:10px 0;"></div>
    <div class="demo-pagination-block">
      <el-pagination v-model:currentPage="currentPage" page-size="10" :page-sizes="[5,10, 20]"
        :small="small" :disabled="disabled" :background="background" layout="total, sizes, prev, pager, next, jumper"
        :total="total" @size-change="handleSizeChange" @current-change="handleCurrentChange" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  components: {

  },
  data() {
    return {
      search: "",
      currentPage: 1,
      total: 10,
      tableData: [
        {
          date: '2016-05-03',
          name: 'Tom',
          address: 'No. 189, Grove St, Los Angeles',
        },
        {
          date: '2016-05-02',
          name: 'Tom',
          address: 'No. 189, Grove St, Los Angeles',
        },
        {
          date: '2016-05-04',
          name: 'Tom',
          address: 'No. 189, Grove St, Los Angeles',
        },
        {
          date: '2016-05-01',
          name: 'Tom',
          address: 'No. 189, Grove St, Los Angeles',
        }]
    }
  },
  methods: {
    handleEdit(a) {
      console.log(a)
    },
    handleSizeChange(){

    },
    handleCurrentChange(){

    }
  }
}
</script>
