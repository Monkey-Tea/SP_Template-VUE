<template>
<div>
  <el-table :data="tableData" stripe>
    <el-table-column prop="id" label="序号" align="center"></el-table-column>
    <el-table-column prop="username" label="用户名" align="center"></el-table-column>
    <el-table-column prop="password" label="密码" align="center"></el-table-column>
    <el-table-column prop="name" label="姓名" align="center"></el-table-column>
    <el-table-column prop="phone" label="电话" align="center"></el-table-column>
    <el-table-column prop="email" label="邮箱" align="center"></el-table-column>
    <el-table-column prop="address" label="地址" align="center"></el-table-column>
    <el-table-column label="头像" align="center">
      <template v-slot="scope">
        <div style="display: flex; align-items: center">
          <el-image style="width: 50px; height: 50px; border-radius: 50%" v-if="scope.row.avatar" :src="scope.row.avatar" :preview-src-list="scope.row.avatar"></el-image>
        </div>
      </template>
    </el-table-column>
    <el-table-column prop="role" label="权限" align="center"></el-table-column>
    <el-table-column label="操作" align="center">
      <template>
        <el-button type="primary" size="mini" plain>编辑</el-button>
        <el-button type="danger" size="mini" plain>删除</el-button>
      </template>
    </el-table-column>
  </el-table>
</div>
</template>
<script>
export default {
  name: "UserView",
  data(){
    return{
      tableData:[]
    }
  },
  created() {
    this.load()
  },
  methods:{
    load(){
      this.$request.get('/user/selectAll').then(res => {
        this.tableData = res.data
          }
      )
    }
  }
}
</script>


<style scoped>

</style>
