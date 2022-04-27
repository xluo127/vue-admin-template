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
    <!-- <div v-for="(item, index) in yjk" :key="index" class="pl dynanmic container" :style="{'--height':TotalHeight}"> -->
    <div v-for="(item, index) in yjk" :key="index" class="pl container">
      <div v-if="index == 0" class="pl1">{{ item.name }}</div>
      <div v-if="index != 0" class="pl2"> {{ index }} : {{ item.name }}</div>
    <!-- 遍历数组 -->
    <!-- <div v-for="(item, index) in arr" :key="index">
      <h1>item {{ item }}</h1>
      <h1>index {{ index }}</h1>
    </div> -->
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
    this.yjk.unshift({ name: '+ 新增元件', desciption: 'button' })
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
* {
  margin-right: 1%;
}
/* .dynanmic {
  height: var(--TotalHeight);
} */
.pl {
  margin-left: 1%;
  padding-left: 1%;
  padding-right: 1%;
  /* border: 2px solid blue; */
}
.form {
  padding-left: 3%;
  padding-top: 30px;
}
.container {
  display: inline-grid;
  grid-row-gap: 15px;
  grid-column-gap: 20px;
  grid-template-columns: repeat(3, 33.3%);
  grid-template-rows: repeat(3, 200px);
  width: 326px;
  height: 184px;
}
.pl1 {
  width: 306px;
  height: 174px;
  border: 2px dashed rgba(0, 0, 0, 0.427);
  font-family: "Microsoft Tai Le Regular", "Microsoft Tai Le";
  font-weight: 400;
  font-style: normal;
  font-size: 14px;
  color: rgba(0, 0, 0, 0.427);
  line-height: 20px;
  text-align: center;
  padding-top: 50%;
}
.pl2 {
  width: 306px;
  height: 174px;
  border: 1px solid rgba(0, 0, 0, 0.427);
  text-align: center;
  padding-top: 50%;
}
</style>
