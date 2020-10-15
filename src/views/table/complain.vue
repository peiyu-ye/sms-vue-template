<template>
  <div class="app-container">
    <div class="tableHtml-top">
      <el-form :inline="true" :model="formInline" class="demo-form-inline">
        <el-form-item label="公司名称">
          <el-input v-model="formInline.value1" placeholder="公司名称" />
        </el-form-item>
        <el-form-item label="投诉类型">
          <el-select v-model="formInline.value3" placeholder="投诉类型">
            <el-option label="全部" value="0" />
            <el-option label="诈骗" value="1" />
            <el-option label="骚扰" value="2" />
            <el-option label="非法催收" value="3" />
            <el-option label="轰炸" value="4" />
            <el-option label="其他" value="5" />
          </el-select>
        </el-form-item>
        <el-form-item label="时间">
          <el-date-picker
            v-model="formInline.value2"
            type="daterange"
            range-separator="-"
            start-placeholder="开始日期"
            end-placeholder="结束日期"
          />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">查询</el-button>
        </el-form-item>
      </el-form>
    </div>
    <div class="tableHtml-bottom">
      <el-table :data="tableData" stripe style="width: 100%">
        <!-- 公司名称	今日投诉	本周投诉	本月投诉	今日短信（送达率）-->
        <el-table-column prop="A" label="公司名称" />
        <el-table-column prop="B" label="今日投诉" />
        <el-table-column v-if="list" prop="C" label="本周投诉" />
        <el-table-column v-if="list" prop="E" label="本月投诉" />
        <el-table-column prop="D" label="今日短信（送达率）" />
      </el-table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: true,
      listLoading: true,
      formInline: {
        value1: '',
        value2: '',
        value3: '0'
      },
      tableData: [
        {
          E: '2020',
          A: '阿里科技有限公司',
          B: '50',
          C: '120',
          D: '50(100%)'
        },
        {
          E: '410',
          A: '特为信息科技有限公司',
          B: '38',
          C: '110',
          D: '38(100%)'
        },
        {
          E: '310',
          A: '众投互联信息技术有限公司',
          B: '28',
          C: '89',
          D: '28(100%)'
        },
        {
          E: '202',
          A: '新形势信息有限公司',
          B: '10',
          C: '25',
          D: '10(100%)'
        },
        {
          E: '101',
          A: '南方科技有限公司',
          B: '5',
          C: '18',
          D: '5(100%)'
        },
        {
          E: '80',
          A: '信润数字科技有限公司',
          B: '5',
          C: '8',
          D: '5(100%)'
        }
      ]
    }
  },
  created() {},
  methods: {
    onSubmit() {
      this.list = !this.formInline.value2
      if (this.formInline.value1) {
        switch (this.formInline.value1) {
          case '众投互联信息技术有限公司':
            this.tableData = [
              {
                E: '310',
                A: '众投互联信息技术有限公司',
                B: '28',
                C: '89',
                D: '28(100%)'
              }
            ]
            break
          case '特为信息科技有限公司':
            this.tableData = [
              {
                E: '410',
                A: '特为信息科技有限公司',
                B: '38',
                C: '110',
                D: '38(100%)'
              }
            ]
            break
          case '阿里科技有限公司':
            this.tableData = [
              {
                E: '2020',
                A: '阿里科技有限公司',
                B: '50',
                C: '120',
                D: '50(100%)'
              }
            ]
            break
          default:
            this.tableData = []
        }
      } else if (this.formInline.value3) {
        switch (this.formInline.value3) {
          case '3':
            this.tableData = [
              {
                E: '310',
                A: '众投互联信息技术有限公司',
                B: '28',
                C: '89',
                D: '28(100%)'
              }
            ]
            break
          case '2':
            this.tableData = [
              {
                E: '410',
                A: '特为信息科技有限公司',
                B: '38',
                C: '110',
                D: '38(100%)'
              },
              {
                E: '2020',
                A: '阿里科技有限公司',
                B: '50',
                C: '120',
                D: '50(100%)'
              }
            ]
            break
          case '5':
            this.tableData = [
              {
                E: '2020',
                A: '阿里科技有限公司',
                B: '50',
                C: '120',
                D: '50(100%)'
              },
              {
                E: '202',
                A: '新形势信息有限公司',
                B: '10',
                C: '25',
                D: '10(100%)'
              },
              {
                E: '101',
                A: '南方科技有限公司',
                B: '5',
                C: '18',
                D: '5(100%)'
              },
              {
                E: '80',
                A: '信润数字科技有限公司',
                B: '5',
                C: '8',
                D: '5(100%)'
              }
            ]
            break
          case '0':
            this.tableData = [
              {
                E: '2020',
                A: '阿里科技有限公司',
                B: '50',
                C: '120',
                D: '50(100%)'
              },
              {
                E: '410',
                A: '特为信息科技有限公司',
                B: '38',
                C: '110',
                D: '38(100%)'
              },
              {
                E: '310',
                A: '众投互联信息技术有限公司',
                B: '28',
                C: '89',
                D: '28(100%)'
              },
              {
                E: '202',
                A: '新形势信息有限公司',
                B: '10',
                C: '25',
                D: '10(100%)'
              },
              {
                E: '101',
                A: '南方科技有限公司',
                B: '5',
                C: '18',
                D: '5(100%)'
              },
              {
                E: '80',
                A: '信润数字科技有限公司',
                B: '5',
                C: '8',
                D: '5(100%)'
              }
            ]
            break
          default:
            this.tableData = []
        }
      } else {
        this.tableData = [
          {
            E: '2020',
            A: '阿里科技有限公司',
            B: '50',
            C: '120',
            D: '50(100%)'
          },
          {
            E: '410',
            A: '特为信息科技有限公司',
            B: '38',
            C: '110',
            D: '38(100%)'
          },
          {
            E: '310',
            A: '众投互联信息技术有限公司',
            B: '28',
            C: '89',
            D: '28(100%)'
          },
          {
            E: '202',
            A: '新形势信息有限公司',
            B: '10',
            C: '25',
            D: '10(100%)'
          },
          {
            E: '101',
            A: '南方科技有限公司',
            B: '5',
            C: '18',
            D: '5(100%)'
          },
          {
            E: '80',
            A: '信润数字科技有限公司',
            B: '5',
            C: '8',
            D: '5(100%)'
          }
        ]
      }
      if (!this.formInline.value1 && !this.formInline.value2) {
        this.tableData = [
          {
            E: '2020',
            A: '阿里科技有限公司',
            B: '50',
            C: '120',
            D: '50(100%)'
          },
          {
            E: '410',
            A: '特为信息科技有限公司',
            B: '38',
            C: '110',
            D: '38(100%)'
          },
          {
            E: '310',
            A: '众投互联信息技术有限公司',
            B: '28',
            C: '89',
            D: '28(100%)'
          },
          {
            E: '202',
            A: '新形势信息有限公司',
            B: '10',
            C: '25',
            D: '10(100%)'
          },
          {
            E: '101',
            A: '南方科技有限公司',
            B: '5',
            C: '18',
            D: '5(100%)'
          },
          {
            E: '80',
            A: '信润数字科技有限公司',
            B: '5',
            C: '8',
            D: '5(100%)'
          }
        ]
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
}
</style>
