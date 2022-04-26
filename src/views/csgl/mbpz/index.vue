<template>
  <div class="mbpz">
    <!-- 表单 -->
    <div class="form">
      <el-form :inline="true" :model="formInline">
        <el-form-item label="测试分类">
          <el-select v-model="formInline.type" placeholder="请选择">
            <el-option label="选项一" value="xx1" />
            <el-option label="选项二" value="xx2" />
          </el-select>
        </el-form-item>
        <el-form-item label="模板名称">
          <el-input v-model="formInline.keyword" placeholder="模糊匹配模板名称" suffix-icon="el-icon-search" />
        </el-form-item>
        <el-form-item>
          <el-button click="onSubmit">查询</el-button>
        </el-form-item>
      </el-form>
    </div>
    <!-- 按钮 -->
    <div class="pl">
      <el-button type="primary">+ 新建模板</el-button>
    </div>
    <!-- 表格 -->
    <div class="pl" style="margin-top:20px">
      <el-table
        :data="tableData"
        border
        style="width: 100%"
      >
        <el-table-column
          fixed
          prop="date"
          label="序号"
          width="80"
        />
        <el-table-column
          prop="name"
          label="测试分类"
          width="160"
        />
        <el-table-column
          prop="province"
          label="模板名称"
          width="220"
        />
        <el-table-column
          prop="city"
          label="模板调用次数"
          width="220"
        />
        <el-table-column
          prop="address"
          label="创建时间"
          width="190"
          sortable
        />
        <el-table-column
          fixed="right"
          label="操作"
          width="100"
        >
          <template slot-scope="scope">
            <el-button type="text" size="small" @click="handleClick(scope.row)">查看</el-button>
            <el-button type="text" size="small">编辑</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
    <!-- 分页 -->
    <div>
      <el-pagination
        class="fixright"
        :current-page="currentPage4"
        :page-sizes="[100, 200, 300, 400]"
        :page-size="100"
        layout="total, sizes, prev, pager, next, jumper"
        :total="400"
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
      />
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      formInline: {
        keyword: '',
        type: ''
      },
      StateOfTasks: '全部'
    }
  }
}
</script>

<style scoped>
.pl {
  padding-left: 3%;
  padding-right: 3%;
}
.form {
  padding-left: 3%;
  padding-top: 30px;
}
.fixright {
  position: absolute;
  right: 2%;
}
</style>
