<template>
  <div class="app-container">
    <div class="tableHtml-top">
      <el-form :inline="true" :model="formInline" class="demo-form-inline">
        <el-form-item label="公司名称">
          <el-input v-model="formInline.value1" placeholder="公司名称" />
        </el-form-item>
        <el-form-item label="时间">
          <el-date-picker
            v-model="formInline.value2"
            type="daterange"
            range-separator="-"
            start-placeholder="开始日期"
            end-placeholder="结束日期"
            @change="reset"
          />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">查询</el-button>
        </el-form-item>
      </el-form>
    </div>
    <div class="tableHtml-bottom">
      <el-table :data="tableData" stripe style="width: 100%">
        <!-- 公司名称	条数	费用（元）	短信剩余条数	月份 -->
        <el-table-column prop="A" label="公司名称" />
        <el-table-column prop="B" label="条数" />
        <el-table-column prop="C" label="费用（元" />
        <el-table-column prop="D" label="短信剩余条数" />
        <el-table-column v-if="list" prop="date" label="月份" />
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
        value2: ''
      },
      tableData: [
        {
          date: '2020-10',
          A: '阿里科技有限公司',
          B: '2000',
          C: '10000',
          D: '8000'
        },
        {
          date: '2020-10',
          A: '特为信息科技有限公司',
          B: '1518',
          C: '20000',
          D: '18482'
        },
        {
          date: '2020-10',
          A: '众投互联信息技术有限公司',
          B: '1510',
          C: '10000',
          D: '8490'
        },
        {
          date: '2020-10',
          A: '新形势信息有限公司',
          B: '1000',
          C: '10000',
          D: '9000'
        },
        {
          date: '2020-10',
          A: '南方科技有限公司',
          B: '500',
          C: '10000',
          D: '9500'
        },
        {
          date: '2020-10',
          A: '信润数字科技有限公司',
          B: '100',
          C: '1000',
          D: '900'
        }
      ],
      tableData2: [
        {
          A: '阿里科技有限公司',
          B: '2000',
          C: '10000',
          D: '8000'
        },
        {
          A: '特为信息科技有限公司',
          B: '1518',
          C: '20000',
          D: '18482'
        },
        {
          date: '2020-10',
          A: '众投互联信息技术有限公司',
          B: '1510',
          C: '10000',
          D: '8490'
        },
        {
          A: '新形势信息有限公司',
          B: '1000',
          C: '10000',
          D: '9000'
        },
        {
          A: '南方科技有限公司',
          B: '500',
          C: '10000',
          D: '9500'
        },
        {
          A: '信润数字科技有限公司',
          B: '100',
          C: '1000',
          D: '900'
        }
      ]
    }
  },
  created() {},
  methods: {
    onSubmit() {
      this.list = !(this.formInline.value2 && this.formInline.value2 != null)
      this.tableData = []
      if (this.formInline.value2) {
        if (this.formInline.value1) {
          switch (this.formInline.value1) {
            case '众投互联信息技术有限公司':
              this.tableData = [
                {
                  A: '众投互联信息技术有限公司',
                  B: '1510',
                  C: '10000',
                  D: '8490'
                }
              ]
              break
            case '特为信息科技有限公司':
              this.tableData = [
                {
                  A: '特为信息科技有限公司',
                  B: '1518',
                  C: '20000',
                  D: '18482'
                }
              ]
              break
            case '阿里科技有限公司':
              this.tableData = [
                {
                  A: '阿里科技有限公司',
                  B: '2000',
                  C: '10000',
                  D: '8000'
                }
              ]
              break
            default:
              this.tableData = this.tableData2
          }
        }
      } else if (this.formInline.value1) {
        switch (this.formInline.value1) {
          case '众投互联信息技术有限公司':
            this.tableData = [
              {
                date: '2020-10',
                A: '众投互联信息技术有限公司',
                B: '1510',
                C: '10000',
                D: '8490'
              }
            ]
            break
          case '特为信息科技有限公司':
            this.tableData = [
              {
                date: '2020-10',
                A: '特为信息科技有限公司',
                B: '1518',
                C: '20000',
                D: '18482'
              }
            ]
            break
          case '阿里科技有限公司':
            this.tableData = [
              {
                date: '2020-10',
                A: '阿里科技有限公司',
                B: '2000',
                C: '10000',
                D: '8000'
              }
            ]
            break
          default:
            this.tableData = [
              {
                date: '2020-10',
                A: '阿里科技有限公司',
                B: '2000',
                C: '10000',
                D: '8000'
              },
              {
                date: '2020-10',
                A: '特为信息科技有限公司',
                B: '1518',
                C: '20000',
                D: '18482'
              },
              {
                date: '2020-10',
                A: '众投互联信息技术有限公司',
                B: '1510',
                C: '10000',
                D: '8490'
              },
              {
                date: '2020-10',
                A: '新形势信息有限公司',
                B: '1000',
                C: '10000',
                D: '9000'
              },
              {
                date: '2020-10',
                A: '南方科技有限公司',
                B: '500',
                C: '10000',
                D: '9500'
              },
              {
                date: '2020-10',
                A: '信润数字科技有限公司',
                B: '100',
                C: '1000',
                D: '900'
              }
            ]
        }
      } else {
        this.tableData = [
          {
            date: '2020-10',
            A: '阿里科技有限公司',
            B: '2000',
            C: '10000',
            D: '8000'
          },
          {
            date: '2020-10',
            A: '特为信息科技有限公司',
            B: '1518',
            C: '20000',
            D: '18482'
          },
          {
            date: '2020-10',
            A: '众投互联信息技术有限公司',
            B: '1510',
            C: '10000',
            D: '8490'
          },
          {
            date: '2020-10',
            A: '新形势信息有限公司',
            B: '1000',
            C: '10000',
            D: '9000'
          },
          {
            date: '2020-10',
            A: '南方科技有限公司',
            B: '500',
            C: '10000',
            D: '9500'
          },
          {
            date: '2020-10',
            A: '信润数字科技有限公司',
            B: '100',
            C: '1000',
            D: '900'
          }
        ]
      }
    },
    reset() {
      if (this.formInline.value2 == null && this.formInline.value1 == null) {
        this.list = !(this.formInline.value2 && this.formInline.value2 != null)
        this.tableData = [
          {
            date: '2020-10',
            A: '阿里科技有限公司',
            B: '2000',
            C: '10000',
            D: '8000'
          },
          {
            date: '2020-10',
            A: '特为信息科技有限公司',
            B: '1518',
            C: '20000',
            D: '18482'
          },
          {
            date: '2020-10',
            A: '众投互联信息技术有限公司',
            B: '1510',
            C: '10000',
            D: '8490'
          },
          {
            date: '2020-10',
            A: '新形势信息有限公司',
            B: '1000',
            C: '10000',
            D: '9000'
          },
          {
            date: '2020-10',
            A: '南方科技有限公司',
            B: '500',
            C: '10000',
            D: '9500'
          },
          {
            date: '2020-10',
            A: '信润数字科技有限公司',
            B: '100',
            C: '1000',
            D: '900'
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
