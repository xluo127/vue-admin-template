<template>
  <div class="cpgl">
    <!-- 表单 -->
    <div class="form">
      <el-form :inline="true" :model="formInline">
        <el-form-item label="产品分类">
          <el-select v-model="formInline.type" placeholder="请选择">
            <el-option label="选项一" value="xx1" />
            <el-option label="选项二" value="xx2" />
          </el-select>
        </el-form-item>
        <el-form-item label="产品名称">
          <el-input v-model="formInline.keyword" placeholder="模糊匹配产品名称" suffix-icon="el-icon-search" />
        </el-form-item>
        <el-form-item>
          <el-button click="onSubmit">查询</el-button>
        </el-form-item>
      </el-form>
    </div>
    <!-- 按钮 -->
    <div class="pl">
      <el-row>
        <el-col :span="12">
          <el-button type="primary">{{ ButtonName1 }}</el-button>
        </el-col>
        <el-col :span="12">
          <el-button class="fixright1" type="primary">{{ ButtonName2 }}</el-button>
        </el-col>
      </el-row>
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
          prop="id"
          label="序号"
          :width="screenWidth*TableWidths.id"
        />
        <el-table-column
          prop="name"
          label="产品名称"
          :width="screenWidth*TableWidths.name"
        />
        <el-table-column
          prop="type"
          label="产品分类"
          :width="screenWidth*TableWidths.type"
        />
        <el-table-column
          prop="time"
          label="创建时间"
          :width="screenWidth*TableWidths.time"
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
        :total="1000"
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
      ButtonName1: `+  添加产品`,
      ButtonName2: '产品分类管理',
      formInline: {
        keyword: '',
        type: ''
      },
      StateOfTasks: '全部',
      tableData: [
        { id: 1, name: '111', type: '111', time: 111 }
      ],
      TableWidths: { id: 0.08, name: 0.2, type: 0.2, time: 0.25 },
      timer: null,
      screenWidth: document.body.clientWidth, // 屏幕宽
      screeHeight: document.body.clientHeight // 屏幕高
    }
  },
  mounted() {
    this.timer = setInterval(this.windowWidthChange, 100) // 每0.1秒刷新一次
  },
  beforeDestroy() {
    clearInterval(this.timer)
  },
  methods: {
    windowWidthChange() {
      this.screenWidth = document.body.clientWidth
      this.screeHeight = document.body.clientHeight
      // console.log(this.screenWidth, this.screeHeight)
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
.fixright1 {
  position: absolute;
  right: 0%;
}
</style>
