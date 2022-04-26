<template>
  <div class="yjk">
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
          <el-button click="onSubmit" type="primary">查询</el-button>
        </el-form-item>
      </el-form>
    </div>
    <!-- 动态元件 -->
    <div class="pl dynanmic" :style="{'--height':TotalHeight}">
      1
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
      StateOfTasks: '全部',
      yjk: [
        {
          name: '实验室资源',
          desciption: '1'
        },
        {
          name: '空间位置',
          desciption: '2'
        },
        {
          name: '播报人声',
          desciption: '3'
        }
      ],
      LenghtOfYjk: 0,
      TotalHeight: '500px'
    }
  },
  created() {
    this.getYjkLength()
    // alert(this.LenghtOfYjk)
  },
  methods: {
    getYjkLength() {
      this.LenghtOfYjk = this.yjk.length
    }
  }
}
</script>

<style scoped>
.dynanmic {
  height: var(--TotalHeight);
}
.pl {
  padding-left: 1%;
  padding-right: 1%;
  border: 2px solid blue;
}
.form {
  padding-left: 3%;
  padding-top: 30px;
}
</style>
