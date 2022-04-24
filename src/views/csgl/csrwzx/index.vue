<template>
  <div class="csrwzx">
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
      <el-row :gutter="20">
        <el-col :span="10">
          <div>
            <el-button type="primary">主要按钮</el-button>
            <el-button type="info" style="color:black">信息按钮</el-button>
            <el-button style="color:black">默认按钮</el-button>
          </div>
        </el-col>
        <el-col :span="4"><div /></el-col>
        <el-col :span="10">
          <div class="fixright">
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
  </div>

</template>
<script>

export default {
  data() {
    return {
      formInline: {
        keyword: '',
        type: '',
        template: ''
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
  right: 0px;
}
</style>
