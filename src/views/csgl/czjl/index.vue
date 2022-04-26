<template>
  <div class="czjl">
    <div>
      <div class="title">操作记录</div>
      <!-- 表单 -->
      <div class="form pl">
        <el-form :inline="true" :model="formInline" class="demo-form-inline">
          <el-form-item label="关键字">
            <el-input v-model="formInline.keyword" placeholder="模糊匹配任务名称" suffix-icon="el-icon-search" />
          </el-form-item>
          <el-form-item label="操作类型">
            <el-select v-model="formInline.type" placeholder="请选择">
              <el-option label="选项一" value="xx1" />
              <el-option label="选项二" value="xx2" />
            </el-select>
          </el-form-item>
          <el-form-item class="fixright">
            <el-button click="onSubmit">查询</el-button>
          </el-form-item>
        </el-form>
      </div>
      <!-- 表格 -->
      <div class="pl" style="margin-top:20px">
        <el-table
          :data="tableData"
          border
          style="width: 100%"
        >
          <el-table-column
            prop="date"
            label="任务名称"
            width="180"
          />
          <el-table-column
            prop="name"
            label="操作类型"
            width="260"
          />
          <el-table-column
            prop="province"
            label="操作内容"
            width="220"
          />
          <el-table-column
            prop="city"
            label="操作员"
            width="220"
          />
          <el-table-column
            prop="address"
            label="操作时间"
            width="190"
          />
          <el-table-column
            fixed="right"
            label="操作"
            width="150"
          >
            <template slot-scope="scope">
              <el-button type="text" size="small" @click="handleClick(scope.row)">查看</el-button>
              <el-button type="text" size="small">编辑</el-button>
            </template>
          </el-table-column>
        </el-table>
      </div>
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
}
.title {
  padding-top: 30px;
  padding-bottom: 15px;
  padding-left: 3%;
  font-size: 18px;
  font-weight: 600;
  color: #000000;
  font-family: "Droid Sans Fallback";
}
</style>
