<template>
  <div class="dashboard-container">
    <div class="dashboard-div">
      <p class="dashboard-text">短信到达情况</p>
      <el-row>
        <el-col :span="16">
          <div class="dashboard-div-left">
            <el-table
              :data="tableData"
              stripe
              style="width: 100%"
              height="calc((100vh - 140px)/2 - 90px )"
            >
              <el-table-column prop="date" label="企业" />
              <el-table-column prop="name" label="发送成功条数" />
              <el-table-column prop="address" label="发送总条数" />
              <el-table-column prop="succeed" label="发送成功率" />
            </el-table>
          </div>
        </el-col>
        <el-col
          :span="8"
        ><div class="dashboard-div-right">
          <div ref="canvas" class="right-canvas" /></div></el-col>
      </el-row>
    </div>
    <div>
      <el-row>
        <el-col :span="16">
          <div class="dashboard-divbtt">
            <p class="dashboard-text">今日投诉情况</p>
            <div class="dashboard-div-left">
              <el-table
                :data="tableData2"
                stripe
                style="width: 100%"
                height="calc((100vh - 140px)/2 - 10px)"
              >
                <el-table-column prop="date" label="企业" />
                <el-table-column prop="tag" label="骚扰方式">
                  <template slot-scope="scope">
                    <el-tag
                      :type="scope.row.tag == '短信' ? 'primary' : 'success'"
                      disable-transitions
                    >{{ scope.row.tag }}</el-tag>
                  </template>
                </el-table-column>
                <el-table-column prop="address" label="数量" />
                <el-table-column prop="name" label="类型分布">
                  <template slot-scope="scope">
                    <pre>{{ scope.row.name.split(",").join("\n") }}</pre>
                  </template>
                </el-table-column>
                <el-table-column prop="succeed" label="码号数量" />
              </el-table>
            </div>
          </div>
        </el-col>
        <el-col :span="8" style="padding-left: 30px;">
          <div class="dashboard-divbtt">
            <p class="dashboard-text">今日短信收入</p>
            <div class="dashboard-div-right">
              <div ref="canvas2" class="right-canvas" />
            </div>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import echarts from 'echarts/lib/echarts'

export default {
  name: 'Dashboard',
  data() {
    return {
      tableData: [
        {
          date: '广东省（运营商）',
          name: '500',
          address: '600',
          succeed: '83.3%'
        },
        {
          date: '广西省（运营商）',
          name: '200',
          address: '250',
          succeed: '80.0%'
        },
        {
          date: '河北省（运营商）',
          name: '100',
          address: '120',
          succeed: '83.3%'
        },
        {
          date: '众投（企业）',
          name: '88',
          address: '100',
          succeed: '88.0%'
        },
        {
          date: '特为（企业）',
          name: '88',
          address: '88',
          succeed: '100%'
        }
      ],
      tableData2: [
        {
          date: '广东省（运营商）',
          name: '诈骗：10,骚扰：50 ,非法催收：20,轰炸：1',
          address: '600',
          succeed: '50000',
          tag: '短信'
        },
        {
          date: '广西省（运营商）',
          name: '诈骗：10,轰炸：1',
          address: '250',
          succeed: '20000',
          tag: '电话'
        },
        {
          date: '河北省（运营商）',
          name: '非法催收：20,轰炸：1',
          address: '120',
          succeed: '8300',
          tag: '短信'
        },
        {
          date: '众投（企业）',
          name: '骚扰：50',
          address: '100',
          succeed: '10000',
          tag: '短信'
        }
      ]
    }
  },
  computed: {
    ...mapGetters(['name'])
  },
  mounted() {
    this.draw()
    this.draw2()
  },
  methods: {
    draw() {
      const myChart = echarts.init(this.$refs.canvas)
      myChart.setOption({
        // option = {
        // backgroundColor: "#fff",
        tooltip: {
          formatter: '{b}{c}'
        },
        series: [
          {
            tooltip: {
              show: false
            },
            name: 'wrap',
            type: 'pie',
            hoverAnimation: false,
            legendHoverLink: false,
            center: ['55%', '70%'],
            radius: ['0%', '7%'],
            z: 5,
            label: {
              normal: {
                show: false,
                position: 'center'
              },
              emphasis: {
                show: false
              }
            },
            labelLine: {
              normal: {
                show: false
              }
            },
            data: [
              {
                value: 100,
                itemStyle: {
                  normal: {
                    color: '#072B79'
                  },
                  emphasis: {
                    color: '#072B79'
                  }
                }
              }
            ]
          },
          {
            tooltip: {
              show: false
            },
            name: 'wrap',
            type: 'pie',
            hoverAnimation: false,
            legendHoverLink: false,
            center: ['55%', '70%'],
            radius: ['6%', '8%'],
            z: 5,
            label: {
              normal: {
                show: false,
                position: 'center'
              },
              emphasis: {
                show: false
              }
            },
            labelLine: {
              normal: {
                show: false
              }
            },
            data: [
              {
                value: 100,
                itemStyle: {
                  normal: {
                    color: '#24D8E7'
                  },
                  emphasis: {
                    color: '#24D8E7'
                  }
                }
              }
            ]
          },
          {
            tooltip: {
              show: false
            },
            name: '刻度',
            type: 'gauge',
            radius: '83%',
            z: 1,
            min: 0,
            max: 1,
            center: ['55%', '70%'],
            splitNumber: 5, // 刻度数量
            startAngle: 180,
            endAngle: 0,
            axisLine: {
              show: true,
              lineStyle: {
                width: 5,
                color: [
                  [0.12, '#E71A6D'],
                  [0.35, '#F88168'],
                  [0.63, '#FBF76B'],
                  [0.8, '#7AD4DF'],
                  [1, '#70C27E']
                ]
              }
            }, // 仪表盘轴线
            axisLabel: {
              show: false
            }, // 刻度标签。
            axisTick: {
              show: true,
              lineStyle: {
                color: 'auto',
                width: 0
              },
              length: -15
            }, // 刻度样式
            splitLine: {
              show: true,
              length: 0,
              lineStyle: {
                color: 'auto',
                width: 2
              }
            }, // 分隔线样式
            detail: {
              show: false
            },
            pointer: {
              show: false
            }
          },
          {
            name: '本期',
            type: 'gauge',
            radius: '80%',
            min: 0,
            max: 1,
            center: ['55%', '70%'],
            data: [
              {
                value: 0.8692,
                name: '通知短信到达率'
              }
            ],
            splitNumber: 12, // 刻度数量
            startAngle: 180,
            endAngle: 0,
            z: 5,
            axisLine: {
              show: true,
              lineStyle: {
                width: 0,
                color: [
                  [0.12, '#E71A6D'],
                  [0.35, '#F88168'],
                  [0.63, '#FBF76B'],
                  [0.8, '#7AD4DF'],
                  [1, '#70C27E']
                ]
              }
            }, // 仪表盘轴线
            axisLabel: {
              show: true,
              color: '#000',
              fontSize: 20,
              distance: -70,
              formatter: function(params) {
                var value = params.toFixed(2)

                if (value === 0.0) {
                  return '危'
                } else if (value === 0.25) {
                  return '差'
                } else if (value === 0.5) {
                  return '中'
                } else if (value === 0.75) {
                  return '良'
                } else if (value === 1.0) {
                  return '优'
                } else {
                  return ''
                }
              }
            }, // 刻度标签。
            axisTick: {
              splitNumber: 10,
              show: true,
              lineStyle: {
                color: 'auto',
                width: 1
              },
              length: 20
            }, // 刻度样式
            splitLine: {
              show: true,
              length: 25,
              lineStyle: {
                color: 'auto',
                width: 3
              }
            }, // 分隔线样式

            itemStyle: {
              normal: {
                color: '#24D8E7' // 指针颜色
              }
            },
            pointer: {
              width: 10,
              length: '80%'
            },
            detail: {
              formatter: function(params) {
                return (params * 100).toFixed(0) + '%'
              },
              fontSize: 30,
              color: '#000',
              offsetCenter: ['0%', '-35%']
            },
            title: {
              offsetCenter: ['0', '-60%'],
              fontSize: 20,
              color: '#000',
              show: true
            }
          }
        ]
        // }
      })
    },
    draw2() {
      const myChart = echarts.init(this.$refs.canvas2)
      var data = [
        {
          name: '广东省（运营商）',
          value: 456
        },
        {
          name: '广西省（运营商）',
          value: 231
        },
        {
          name: '众投（企业）',
          value: 121
        }
      ]
      myChart.setOption({
        // option = {
        color: [
          '#5f45ff',
          '#02cdff',
          '#f9e264',
          '#f47a75',
          '#009db2',
          '#024b51- 0780cf',
          '#765005'
        ],
        title: {
          text: 808 + '元',
          subtext: '总计',
          textStyle: {
            color: '#000',
            fontSize: 30
          },
          subtextStyle: {
            fontSize: 20,
            color: ['#ff9d19']
          },
          x: 'center',
          y: 'center'
        },
        tooltip: {
          trigger: 'item',
          formatter: '{b}<br/> {c}元({d}%)'
        },
        series: [
          // 主要展示层的
          {
            radius: ['50%', '90%'],
            center: ['50%', '50%'],
            type: 'pie',
            label: {
              position: 'inner',
              formatter: '{b}'
            },
            labelLine: {
              normal: {
                show: true,
                length: 20,
                length2: 45
              },
              emphasis: {
                show: true
              }
            },
            data: data
          },
          // 边框的设置
          {
            radius: ['45%', '50%'],
            center: ['50%', '50%'],
            type: 'pie',
            label: {
              normal: {
                show: false
              },
              emphasis: {
                show: false
              }
            },
            labelLine: {
              normal: {
                show: false
              },
              emphasis: {
                show: false
              }
            },
            animation: false,
            tooltip: {
              show: false
            },
            data: [
              {
                value: 1,
                itemStyle: {
                  color: 'rgba(0,0,0,0.3)'
                }
              }
            ]
          }
        ]
        // }
      })
    }
  }
}
</script>
<style>
.el-table .cell {
  white-space: pre-line;
}
</style>
<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px 30px 0 30px;
  }
  &-text {
    font-size: 20px;
    margin: 6px 0 0 6px;
    text-align: left;
  }
  &-div {
    width: 100%;
    height: calc((100vh - 140px) / 2 - 40px);
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

    &-left {
      width: 100%;
      display: inline-block;
    }
    &-right {
      display: inline-block;
      width: 100%;
      .right-canvas {
        // height: 350px;
        height: calc((100vh - 140px) / 2 - 65px);
      }
    }
  }
  &-divbtt {
    display: inline-block;
    margin-top: 30px;
    width: 100%;
    height: calc((100vh - 140px) / 2 + 40px);
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

    &-left {
      width: 100%;
      display: inline-block;
    }
    &-right {
      display: inline-block;
      width: 100%;
      .right-canvas {
        // height: 350px;
        height: calc((100vh - 140px) / 2 - 90px);
      }
    }
  }
}

</style>
