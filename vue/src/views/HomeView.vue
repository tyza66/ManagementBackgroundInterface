<template>
  <div class="home" style="width: 100%;padding: 10px">
    <div style="margin:10px 0;">
      <el-button type="primary" @click="add">新增</el-button>
      <el-input clearable v-model="search" placeholder="请输入内容" style="width:20%;margin-left:10px;"></el-input>
      <el-button type="primary" style="margin-left:10px;" @click="load()">查询</el-button>
    </div>
    <el-table :data="tableData" border stripe style="width: 100%;">
      <el-table-column prop="id" label="ID" sortable />
      <el-table-column prop="username" label="用户名" />
      <el-table-column prop="nickName" label="昵称" />
      <el-table-column prop="age" label="年龄" />
      <el-table-column prop="sex" label="性别" />
      <el-table-column prop="address" label="地址" />
      <el-table-column fixed="right" label="操作" width="140">
        <template #default="scope">
          <el-button type="text" size="small" @click="handleEdit(scope.row)">编辑</el-button>
          <el-popconfirm title="你确定要删除吗?" @confirm="handleDelete(scope.row.id)">
            <template #reference>
              <el-button type="text" size="small">删除</el-button>
            </template>
          </el-popconfirm>
        </template>
      </el-table-column>
    </el-table>
    <div style="margin:10px 0;"></div>
    <div class="demo-pagination-block">
      <el-pagination v-model:currentPage="currentPage" v-model:page-size="pageSize" :page-sizes="[5, 10, 20]"
        :small="small" :disabled="disabled" :background="background" layout="total, sizes, prev, pager, next, jumper"
        :total="total" @size-change="handleSizeChange" @current-change="handleCurrentChange" />
      <el-dialog v-model="dialogVisible" title="添加" width="30%">
        <el-form :model="form" label-width="120px">
          <el-form-item label="用户名">
            <el-input v-model="form.username" style="width:80%;"></el-input>
          </el-form-item>
          <el-form-item label="昵称">
            <el-input v-model="form.nickName" style="width:80%;"></el-input>
          </el-form-item>
          <el-form-item label="年龄">
            <el-input v-model="form.age" style="width:80%;"></el-input>
          </el-form-item>
          <el-form-item label="性别">
            <el-radio v-model="form.sex" label="男">男</el-radio>
            <el-radio v-model="form.sex" label="女">女</el-radio>
            <el-radio v-model="form.sex" label="未知">未知</el-radio>
          </el-form-item>
          <el-form-item label="地址">
            <el-input type="textarea" v-model="form.address" style="width:80%;"></el-input>
          </el-form-item>
        </el-form>
        <template #footer>
          <span class="dialog-footer">
            <el-button @click="dialogVisible = false">取消</el-button>
            <el-button type="primary" @click="save()">确定</el-button>
          </span>
        </template>
      </el-dialog>

    </div>
  </div>
</template>

<script>
import { request } from '@/utils/request';

export default {
  name: 'HomeView',
  components: {

  },
  data() {
    return {
      form: {},
      dialogVisible: false,
      search: "",
      currentPage: 1,
      pageSize: 10,
      total: 0,
      tableData: []
    }
  },
  created() {
    this.load();
  },
  methods: {
    load() {
      request.get("/user", {
        params: {
          pageNum: this.currentPage,
          pageSize: this.pageSize,
          search: this.search
        }
      }).then(res => {
        //console.log(res);
        this.tableData = res.data.records;
        this.total = res.data.total;
      })
    },
    add() {
      this.dialogVisible = true;
      this.form = {};
    },
    save() {
      if (this.form.id) {
        request.put("/user", this.form).then(res => {
          if (res.code == '0') {
            this.$message({
              type: "success",
              message: "更新成功"
            });
          } else {
            this.$message({
              type: "error",
              message: res.msg
            });
          }
        })
      } else {
        request.post("/user", this.form).then(res => {
          if (res.code == '0') {
            this.$message({
              type: "success",
              message: "新增成功"
            });
          } else {
            this.$message({
              type: "error",
              message: res.msg
            });
          }
        })
      }
      this.load();
      this.dialogVisible = false;
    },
    handleEdit(row) {
      //深拷贝，为了防止更改了本地变量里面的form
      this.form = JSON.parse(JSON.stringify(row));
      this.dialogVisible = true;
    },
    handleSizeChange(pageSize) { //改变当前每页的个数触发
      //this.pageSize = pageSize; 我使用了双向绑定
      this.load();
    },
    handleCurrentChange(pageNum) {  //改变当前页码触发
      //this.currentPage = pageNum; 同上
      this.load();
    },
    handleDelete(id) {
      console.log(id);
      request.delete("/user/" + id).then(res => {
        if (res.code == '0') {
            this.$message({
              type: "success",
              message: "删除成功"
            });
          } else {
            this.$message({
              type: "error",
              message: res.msg
            });
          }
      })
      this.load();
    }
  }
}
</script>
