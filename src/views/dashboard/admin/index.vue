<template>
  <div class="dashboard-editor-container">

    <panel-group />

    <el-row :gutter="32">
      <el-col :xs="24" :sm="24" :lg="10">
        <div class="chart-wrapper">
          <line-chart />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="7">
        <div class="chart-wrapper">
          calendar
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="7">
        <div class="chart-wrapper">
          <bar-chart />
        </div>
      </el-col>
    </el-row>

    <el-row :gutter="32">
      <el-col :xs="24" :sm="24" :lg="7">
        <div class="chart-wrapper">
          <bar-chartread />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="10">
        <div class="chart-wrapper">
          <line-chartreadinteract />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="7">
        <div class="chart-wrapper">
          <radar-chart />
        </div>
      </el-col>
    </el-row>

    <el-row :gutter="32">
      <el-col :xs="24" :sm="24" :lg="7">
        <div class="chart-wrapper">
          <bar-chartactivity />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="17">
        <div class="chart-wrapper">
          <pie-chartbehave />
        </div>
      </el-col>
    </el-row>

    <el-row :gutter="8">
      <el-col :xs="{span: 24}" :sm="{span: 24}" :md="{span: 24}" :lg="{span: 12}" :xl="{span: 12}" style="padding-right:8px;margin-bottom:30px;">
        <transaction-table />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <todo-list />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <box-card />
      </el-col>
    </el-row>
  </div>
</template>

<script>
import PanelGroup from './components/PanelGroup'
import LineChart from './components/LineChart'
import LineChartreadinteract from './components/LineChartreadinteract'
import RaddarChart from './components/RaddarChart'
import PieChart from './components/PieChart'
import BarChart from './components/BarChart'
import BarChartread from './components/BarChartread'
import BarChartactivity from './components/BarChartactivity'
import RadarChart from './components/RadarChart'
import PieChartbehave from './components/PieChartbehave'
import TransactionTable from './components/TransactionTable'
import TodoList from './components/TodoList'
import BoxCard from './components/BoxCard'

export default {
  name: 'DashboardAdmin',
  components: {
    PanelGroup,
    LineChart,
    LineChartreadinteract,
    RaddarChart,
    PieChart,
    BarChart,
    BarChartread,
    BarChartactivity,
    RadarChart,
    PieChartbehave,
    TransactionTable,
    TodoList,
    BoxCard
  },
  data() {
    return {

    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard-editor-container {
  padding: 32px;
  background-color: rgb(240, 242, 245);
  position: relative;

  .chart-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;
  }
}

@media (max-width:1024px) {
  .chart-wrapper {
    padding: 8px;
  }
}
</style>
