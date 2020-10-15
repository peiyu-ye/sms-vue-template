<template>
  <div class="app-container">
    <div class="tableHtml-top">
      <el-form :inline="true" :model="formInline" class="demo-form-inline">
        <el-form-item label="公司名称">
          <el-input
            v-model="formInline.value1"
            placeholder="公司名称"
          />
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
        <!-- 公司名称	送达量	到达率	月环比	月份 -->
        <el-table-column prop="A" label="公司名称" />
        <el-table-column prop="E" label="送达量" />
        <el-table-column prop="B" label="到达率" />
        <el-table-column v-if="list" prop="C" label="月环比">
          <template slot-scope="scope">
            <el-tag
              :type="scope.row.C === '下降' ? 'danger' : 'success'"
              disable-transitions
            >{{ scope.row.C === '下降' ? '↓' : '↑' }}</el-tag>
          </template>
        </el-table-column>
        <el-table-column v-if="list" prop="D" label="月份" />
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
          E: '2020',
          A: '阿里科技有限公司',
          B: '89%',
          C: '下降',
          D: '2020-10'
        },
        {
          E: '410',
          A: '特为信息科技有限公司',
          B: '100%',
          C: '增长',
          D: '2020-10'
        }, {
          E: '310',
          A: '众投互联信息技术有限公司',
          B: '100%',
          C: '增长',
          D: '2020-10'
        }, {
          E: '202',
          A: '新形势信息有限公司',
          B: '100%',
          C: '增长',
          D: '2020-10'
        }, {
          E: '101',
          A: '南方科技有限公司',
          B: '100%',
          C: '增长',
          D: '2020-10'
        }, {
          E: '80',
          A: '信润数字科技有限公司',
          B: '100%',
          C: '增长',
          D: '2020-10'
        }
      ]
    }
  },
  created() {
  },
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
                B: '100%',
                C: '增长',
                D: '2020-10'
              }
            ]
            break
          case '阿里科技有限公司':
            this.tableData = [
              {
                E: '2020',
                A: '阿里科技有限公司',
                B: '89%',
                C: '下降',
                D: '2020-10'
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
            B: '89%',
            C: '下降',
            D: '2020-10'
          },
          {
            E: '410',
            A: '特为信息科技有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
          }, {
            E: '310',
            A: '众投互联信息技术有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
          }, {
            E: '202',
            A: '新形势信息有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
          }, {
            E: '101',
            A: '南方科技有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
          }, {
            E: '80',
            A: '信润数字科技有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
          }
        ]
      }
      if (!this.formInline.value1 && !this.formInline.value2) {
        this.tableData = [
          {
            E: '2020',
            A: '阿里科技有限公司',
            B: '89%',
            C: '下降',
            D: '2020-10'
          },
          {
            E: '410',
            A: '特为信息科技有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
          }, {
            E: '310',
            A: '众投互联信息技术有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
          }, {
            E: '202',
            A: '新形势信息有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
          }, {
            E: '101',
            A: '南方科技有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
          }, {
            E: '80',
            A: '信润数字科技有限公司',
            B: '100%',
            C: '增长',
            D: '2020-10'
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
