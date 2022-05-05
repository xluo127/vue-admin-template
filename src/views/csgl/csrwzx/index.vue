<template>
  <div class="csrwzx">
    <div v-if="!child1 && true">
      <!-- 任务信息 -->
      <div>
        <el-divider />
        <el-row>
          <el-col :span="7">
            <div class="info">
              <div class="upinfo">
                <p class="upp">待办任务</p>
              </div>
              <div class="downinfo">
                8个任务
              </div>
            </div>
          </el-col>
          <!-- 自行写分割线 -->
          <el-col :span="1">
            <div class="info divider" />
          </el-col>
          <el-col :span="7">
            <div class="info">
              <div class="upinfo">
                <p class="upp">本周任务平均处理时间</p>
              </div>
              <div class="downinfo">
                32分钟
              </div>
            </div>
          </el-col>
          <el-col :span="1">
            <div class="info divider" />
          </el-col>
          <el-col :span="7">
            <div class="info">
              <div class="upinfo">
                <p class="upp">本周完成任务数</p>
              </div>
              <div class="downinfo">
                24个任务
              </div>
            </div>
          </el-col>
        </el-row>
        <el-divider />
      </div>
      <div class="rwlb">
        任务列表
      </div>
      <!-- 表单 -->
      <div class="form">
        <el-form :inline="true" :model="formInline" class="demo-form-inline">
          <el-form-item label="关键字">
            <el-input v-model="formInline.keyword" placeholder="模糊匹配信息名称或描述" suffix-icon="el-icon-search" />
          </el-form-item>
          <el-form-item label="产品分类">
            <el-select v-model="formInline.type" placeholder="请选择">
              <el-option label="选项一" value="xx1" />
              <el-option label="选项二" value="xx2" />
            </el-select>
          </el-form-item>
          <el-form-item label="任务模板">
            <el-select v-model="formInline.template" placeholder="请选择">
              <el-option label="选项一" value="xx1" />
              <el-option label="选项二" value="xx2" />
            </el-select>
          </el-form-item>
          <el-form-item class="fixright">
            <el-button click="onSubmit">查询</el-button>
          </el-form-item>
        </el-form>
      </div>
      <!-- 筛选和操作任务 -->
      <div class="pl">
        <el-row>
          <el-col :span="10">
            <div>
              <router-link to="/csgl/csrwzx/xjrw" custom style="padding-right:10px">
                <el-button type="primary">新增任务</el-button>
              </router-link>
              <el-button type="info" style="color:black">全部暂停</el-button>
              <el-button style="color:black">全部启动</el-button>
            </div>
          </el-col>
          <el-col :span="4" />
          <el-col :span="10">
            <div class="fixright1">
              <el-radio-group v-model="StateOfTasks">
                <el-radio-button label="全部" />
                <el-radio-button label="进行中" />
                <el-radio-button label="等待中" />
                <el-radio-button label="我的任务" />
              </el-radio-group>
            </div>
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
            prop="id"
            label="序号"
            width="80"
          />
          <el-table-column
            prop="info"
            label="任务信息"
            width="160"
          />
          <el-table-column
            prop="ptype"
            label="产品分类"
            width="120"
          />
          <el-table-column
            prop="ttype"
            label="测试分类"
            width="120"
          />
          <el-table-column
            prop="user"
            label="用户"
            width="90"
          />
          <el-table-column
            prop="time"
            label="时间"
            width="180"
          >
            <template slot-scope="scope">
              开始时间:<br>
              {{ scope.row.time }}
            </template>
          </el-table-column>
          <el-table-column
            prop="state"
            label="状态"
            width="240"
          >
            <template slot-scope="scope">
              <el-progress v-if="scope.row.state.type === 'pause'" :percentage="scope.row.state.percentage" />
            </template>
          </el-table-column>
          <el-table-column
            fixed="right"
            label="操作"
            width="130"
          >
            <template slot-scope="scope">
              <el-button type="text" size="small" @click="handleClick(scope.row)">查看结果</el-button>
              <el-button v-if="scope.row.state.type === 'pause'" type="text" size="small">暂停</el-button>
              <el-button v-if="!scope.row.state.type === 'pause'" type="text" size="small">更多</el-button>
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
    <div v-if="child1">
      <router-view />
    </div>
  </div>
</template>
<script>

export default {
  data() {
    return {
      child1: this.$route.path.includes('/xjrw'),
      formInline: {
        keyword: '',
        type: '',
        template: ''
      },
      StateOfTasks: '全部',
      tableData: [
        { id: 1, info: '紧急任务', ptype: '智能音箱', ttype: '语音交互', user: '交互测试-朱洁', time: '2022-3-25 14:00', state: { percentage: '60', type: 'pause' }}
      ]
    }
  },
  methods: {
    test1(aaa) {
      console.log(aaa)
    }
  }
}
</script>

<style scoped>
.pl {
  padding-left: 3%;
  padding-right: 3%;
}
.info {
  height: 70px;
}
.upinfo {
  height: 50%;
  text-align: center;
  font-size: 15px;
  padding-bottom: 0;
  position: relative;
}
.upp {
  position: absolute;
  /* 设置宽度后用margin让元素水平居中 */
  width: 100%;
  margin: 0 auto;
  bottom: 10px;
  padding: 0px;
  color: #8d8d8d;
  font-weight: 200;
}
.downinfo {
  height: 50%;
  text-align: center;
  font-size: 24px;
  color: #000000;
  font-weight: 400;
  font-family: "DejaVu Sans";
}
.divider {
  width: 1px;
  /* border: 1px solid #8d8d8d; */
  background-color: #d1c8c8;
}
.rwlb {
  padding-left: 3%;
  font-size: 18px;
  font-weight: 600;
  color: #000000;
  font-family: "Droid Sans Fallback";
}
.form {
  padding-left: 3%;
  padding-top: 10px;
  position: relative;
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
