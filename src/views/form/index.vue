<template>
  <div class="app-container">
    <div class="tableHtml-top">
      <el-form :inline="true" :model="formInline" class="demo-form-inline">
        <el-form-item label="公司名称">
          <el-select v-model="formInline.value1" placeholder="公司名称" @change="onSubmit">
            <el-option
              label="众投互联信息技术有限公司"
              value="众投互联信息技术有限公司"
            />
            <el-option
              label="特为信息科技有限公司"
              value="特为信息科技有限公司"
            />
            <el-option
              label="阿里科技有限公司"
              value="阿里科技有限公司"
            />
            <el-option
              label="新形势信息有限公司"
              value="新形势信息有限公司"
            />
            <el-option
              label="南方科技有限公司"
              value="南方科技有限公司"
            />
            <el-option
              label="信润数字科技有限公司"
              value="信润数字科技有限公司"
            />
          </el-select>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">查询</el-button>
        </el-form-item>
      </el-form>
    </div>
    <div class="tableHtml-bottom">
      <el-row>
        <el-col :span="14" :offset="6">
          <p>{{ formInline.value1 }}</p>
          <div class="tableHtml-bottom-cent">
            <p class="p-text">
              频率：<span class="number"> {{ value2 }} </span> 次/天（最大每天发送次数）
            </p>
            <p class="p-text">规则：</p>
            <p class="p-text">
              投诉总量达到<span class="number"> {{ value3 }} </span> 次/天时提醒
            </p>
            <p class="p-text">
              诈骗投诉达到<span class="number"> {{ value4 }} </span> 次/天时提醒
            </p>
            <p class="p-text">
              轰炸投诉达到<span class="number"> {{ value5 }} </span> 次/天时提醒
            </p>
            <p class="p-text">
              重复投诉达到<span class="number"> {{ value6 }} </span> 次/天时提醒
            </p>
            <p class="p-text">
              骚扰投诉达到<span class="number"> {{ value7 }} </span> 次/天时提醒
            </p>
            <p class="p-text">
              非法催收投诉达到<span class="number"> {{ value8 }} </span> 次/天时提醒
            </p>
            <el-button
              type="primary"
              class="button-plain"
              @click="dialogVisible = true"
            >更新配置</el-button>
          </div>
        </el-col>
      </el-row>
    </div>
    <el-dialog
      title="更新配置"
      :visible.sync="dialogVisible"
      width="500px"
      :before-close="handleClose"
    >
      <div>
        <p class="p-text">
          频率：
          <el-input v-model="value2" placeholder="请输入整数" />
          次/天（最大每天发送次数）
        </p>
        <p class="p-text">规则：</p>
        <p class="p-text">
          投诉总量达到
          <el-input v-model="value3" placeholder="请输入整数" />
          次/天时提醒
        </p>
        <p class="p-text">
          诈骗投诉达到
          <el-input v-model="value4" placeholder="请输入整数" />
          次/天时提醒
        </p>
        <p class="p-text">
          轰炸投诉达到
          <el-input v-model="value5" placeholder="请输入整数" />
          次/天时提醒
        </p>
        <p class="p-text">
          重复投诉达到
          <el-input v-model="value6" placeholder="请输入整数" />
          次/天时提醒
        </p>
        <p class="p-text">
          骚扰投诉达到
          <el-input v-model="value7" placeholder="请输入整数" />
          次/天时提醒
        </p>
        <p class="p-text">
          非法催收投诉达到
          <el-input v-model="value8" placeholder="请输入整数" />
          次/天时提醒
        </p>
      </div>
      <span slot="footer" class="dialog-footer">
        <el-button @click="handleClose">取 消</el-button>
        <el-button
          type="primary"
          @click="handleSubmit"
        >确 定</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dialogVisible: false,
      list: true,
      listLoading: true,
      formInline: {
        value1: '众投互联信息技术有限公司'
      },
      value2: 5,
      value3: 15,
      value4: 1,
      value5: 6,
      value6: 5,
      value7: 5,
      value8: 5
    }
  },
  created() {},
  methods: {
    onSubmit() {
      if (this.formInline.value1) {
        switch (this.formInline.value1) {
          case '特为信息科技有限公司':
            this.value2 = 5
            this.value3 = 10
            this.value4 = 1
            this.value5 = 4
            this.value6 = 6
            this.value7 = 3
            this.value8 = 8
            break
          case '阿里科技有限公司':
            this.value2 = 5
            this.value3 = 20
            this.value4 = 3
            this.value5 = 7
            this.value6 = 6
            this.value7 = 5
            this.value8 = 8
            break
          default:
            this.value2 = 5
            this.value3 = 15
            this.value4 = 1
            this.value5 = 6
            this.value6 = 5
            this.value7 = 5
            this.value8 = 5
        }
      } else {
        this.$message({
          message: '请输入搜索内容',
          type: 'warning'
        })
      }
    },
    handleClose(done) {
      this.$confirm('确认关闭？')
        .then(_ => {
          this.dialogVisible = false
          done()
        })
        .catch(_ => {})
    },
    handleSubmit(done) {
      this.$confirm('确认更改提交吗？')
        .then(_ => {
          this.$message({
            message: '更改成功',
            type: 'success'
          })
          this.dialogVisible = false
          return done()
        })
        .catch(_ => {})
    }
  }
}
</script>
<style>
.p-text .el-input .el-input__inner{
  /* width: 30%; */
  display: inline-block;
}
.p-text .el-input{
  width: 30%;
  display: inline-block;
}
</style>
<style lang="scss" scoped>
.tableHtml {
  &-top {
    margin-bottom: 24px;
  }

  &-bottom {
    p {
      font-size: 20px;
      color: rgba(0, 0, 0, 0.8);
    }
    &-cent {
      text-align: center;
      width: 60%;
      height: 420px;
      border-color: rgb(255, 254, 254);
      border-width: 1px;
      border-style: solid;
      box-shadow: rgba(0, 0, 0, 0.4) 0px 2px 6px 0px;
      border-radius: 3px;
      font-size: 16px;
      padding: 0px;
      text-align: center;
      line-height: 23px;
      font-weight: normal;
      font-style: normal;
      opacity: 1;
      transform: rotate(0deg);
      padding: 4px;
      .p-text {
        margin-bottom: 1rem;
        font-size: 18px;
        color: rgba(0, 0, 0, 0.8);
        text-align: left;
        padding-left: 3rem;
      }
      .number {
        font-size: 20px;
        color: royalblue;
        border-bottom: 1px solid #000;
        padding-bottom: 5px;
        padding-left: 16px;
        padding-right: 16px;
      }
    }
    .button-plain {
      margin-left: 75%;
      margin-top: 1rem;
    }
  }
}
</style>
