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
      <p>{{ formInline.value1 }}</p>
      <el-row>
        <el-col :span="8">
          <div class="tableHtml-bottom-left">
            <p class="p-text">
              单价：<span class="number"> {{ rule.value2 }} </span> &nbsp;&nbsp;
              元/条
            </p>
            <p class="p-text">
              充值金额：
              <span class="number"> {{ rule.value3 }} </span> &nbsp;&nbsp; 元
              <span class="commit-text">（可为负数，负数时为扣减条数）</span>
            </p>
            <p class="p-text">
              实际充值条数： <span class="number"> {{ rule.value4 }} </span>
              <span class="commit-text">（根据金额及单件计算）</span>
            </p>
            <p class="p-text">
              充值备注：
              <el-input
                v-model="rule.commit"
                type="textarea"
                :rows="4"
                placeholder="请输入内容"
              />
            </p>
          </div>
        </el-col>
        <el-col :span="16">
          <div class="tableHtml-bottom-right">
            <p class="p-text">历史充值记录</p>
            <el-table :data="tableData" stripe style="width: 100%">
              <!-- 日期	金额	单价	条数	备注 -->
              <el-table-column prop="date" label="日期" />
              <el-table-column prop="money" label="金额" />
              <el-table-column prop="price" label="单价" />
              <el-table-column prop="number" label="条数" />
              <el-table-column prop="comment" label="备注" />
            </el-table>
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
      listLoading: true,
      formInline: {
        value1: '众投互联信息技术有限公司'
      },
      rule: {
        value2: 1,
        value3: 700,
        value4: 700,
        commit: '短信充值'
      },
      tableData: [
        {
          date: '2020-10-01',
          money: '500',
          price: '1',
          number: '500',
          comment: '短信充值'
        },
        {
          date: '2020-10-03',
          money: '70',
          price: '1',
          number: '70',
          comment: '短信充值'
        },
        {
          date: '2020-10-05',
          money: '50',
          price: '1',
          number: '50',
          comment: '短信充值'
        },
        {
          date: '2020-10-06',
          money: '500',
          price: '1',
          number: '500',
          comment: '短信充值'
        },
        {
          date: '2020-10-07',
          money: '500',
          price: '1',
          number: '500',
          comment: '短信充值'
        },
        {
          date: '2020-10-10',
          money: '1500',
          price: '1',
          number: '1500',
          comment: '短信充值'
        },
        {
          date: '2020-10-12',
          money: '700',
          price: '1',
          number: '700',
          comment: '短信充值'
        }
      ]
    }
  },
  created() {},
  methods: {
    onSubmit() {
      if (this.formInline.value1) {
        switch (this.formInline.value1) {
          case '特为信息科技有限公司':
            this.rule = {
              value2: 1,
              value3: 2000,
              value4: 2000,
              commit: '短信充值业务'
            }
            this.tableData = [
              {
                date: '2020-10-01',
                money: '1100',
                price: '1',
                number: '1100',
                comment: '短信充值业务'
              },
              {
                date: '2020-10-04',
                money: '700',
                price: '1',
                number: '700',
                comment: '短信充值'
              },
              {
                date: '2020-10-06',
                money: '500',
                price: '1',
                number: '500',
                comment: '短信充值业务'
              },
              {
                date: '2020-10-08',
                money: '1000',
                price: '1',
                number: '1000',
                comment: '短信充值'
              },
              {
                date: '2020-10-12',
                money: '1500',
                price: '1',
                number: '1500',
                comment: '短信充值'
              },
              {
                date: '2020-10-14',
                money: '700',
                price: '1',
                number: '700',
                comment: '短信充值'
              }
            ]
            break
          case '阿里科技有限公司':
            this.rule = {
              value2: 1,
              value3: 5000,
              value4: 5000,
              commit: '充值业务'
            }
            this.tableData = [
              {
                date: '2020-10-01',
                money: '1100',
                price: '1',
                number: '1100',
                comment: '充值业务'
              },
              {
                date: '2020-10-04',
                money: '700',
                price: '1',
                number: '700',
                comment: '充值'
              },
              {
                date: '2020-10-06',
                money: '500',
                price: '1',
                number: '500',
                comment: '充值业务'
              },
              {
                date: '2020-10-08',
                money: '1000',
                price: '1',
                number: '1000',
                comment: '充值'
              },
              {
                date: '2020-10-12',
                money: '1500',
                price: '1',
                number: '1500',
                comment: '充值'
              },
              {
                date: '2020-10-14',
                money: '5000',
                price: '1',
                number: '5000',
                comment: '充值'
              }
            ]
            break
          default:
            this.rule = {
              value2: 1,
              value3: 700,
              value4: 700,
              commit: '短信充值'
            }
            this.tableData = [
              {
                date: '2020-10-01',
                money: '500',
                price: '1',
                number: '500',
                comment: '短信充值'
              },
              {
                date: '2020-10-03',
                money: '70',
                price: '1',
                number: '70',
                comment: '短信充值'
              },
              {
                date: '2020-10-05',
                money: '50',
                price: '1',
                number: '50',
                comment: '短信充值'
              },
              {
                date: '2020-10-06',
                money: '500',
                price: '1',
                number: '500',
                comment: '短信充值'
              },
              {
                date: '2020-10-07',
                money: '500',
                price: '1',
                number: '500',
                comment: '短信充值'
              },
              {
                date: '2020-10-10',
                money: '1500',
                price: '1',
                number: '1500',
                comment: '短信充值'
              },
              {
                date: '2020-10-12',
                money: '700',
                price: '1',
                number: '700',
                comment: '短信充值'
              }
            ]
        }
      } else {
        this.$message({
          message: '请输入搜索内容',
          type: 'warning'
        })
      }
    }
  }
}
</script>
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

    &-left {
      display: inline-block;
      width: 100%;
      min-height: calc(100vh - 500px);
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
      .number {
        font-size: 20px;
        color: royalblue;
        border-bottom: 1px solid #000;
        padding-bottom: 5px;
        padding-left: 22px;
        padding-right: 22px;
      }
      .commit-text {
        display: block;
        font-size: 12px;
        color: rgba(0, 0, 0, 0.4);
        margin-top: 0.5rem;
      }
    }

    &-right {
      display: inline-block;
      margin-left: 4%;
      width: 96%;
      min-height: calc(100vh - 500px);
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
    }
    .p-text {
      margin-bottom: 1.5rem;
      font-size: 18px;
      color: rgba(0, 0, 0, 0.8);
      text-align: left;
      padding-left: 1rem;
    }
  }
}
</style>
