<template>
  <el-row :gutter="40" class="panel-group">
    <el-col :xs="12" :sm="12" :lg="5" class="card-panel-col">
      <div class="card-panel">
        <div class="card-panel-date">2019-12-02 9:9更新</div>
        <div class="card-panel-body">
          <div class="card-panel-description">我的成绩</div>
          <div class="card-panel-result">95分</div>
        </div>
        <div class="card-panel-bottom">
          <div class="card-panel-info">位次在<span class="card-panel-num">前10%</span>，继续保持~</div>
        </div>
      </div>
    </el-col>
    <el-col :xs="12" :sm="12" :lg="5" class="card-panel-col">
      <div class="card-panel">
        <div class="card-panel-date" />
        <div class="card-panel-body">
          <div class="card-panel-description">任务完成度</div>
          <div class="card-panel-result">90%</div>
        </div>
        <div class="card-panel-bottom">
          <div class="card-panel-info">位次在<span class="card-panel-num">前10%</span>，继续保持~</div>
        </div>
      </div>
    </el-col>
    <el-col :xs="12" :sm="12" :lg="5" class="card-panel-col">
      <div class="card-panel">
        <div class="card-panel-date" />
        <div class="card-panel-body">
          <div class="card-panel-description">收到预警</div>
          <div class="card-panel-result">5条</div>
        </div>
        <div class="card-panel-bottom">
          <div class="card-panel-info">预警严重程度4星</div>
        </div>
      </div>
    </el-col>
    <el-col :xs="12" :sm="12" :lg="5" class="card-panel-col">
      <div class="card-panel">
        <div class="card-panel-date" />
        <div class="card-panel-body">
          <div class="card-panel-description">我的学习报告</div>
          <div class="card-panel-result" />
        </div>
        <div class="card-panel-bottomDate">
          <div class="card-panel-calendar" />
        </div>
      </div>
    </el-col>
    <el-col :xs="12" :sm="12" :lg="4" class="card-panel-col">
      <div class="card-panel">
        <div class="card-panel-studyStyle">
          <div class="card-panel-title">我的学习风格</div>
          <div class="card-panel-browse">查看</div>
        </div>
      </div>
    </el-col>
  </el-row>
</template>

<script>
// import CountTo from 'vue-count-to'

export default {
  components: {

  },
  methods: {

  }
}
</script>

<style lang="scss" scoped>
.panel-group {
  margin-top: 18px;

  .card-panel-col {
    margin-bottom: 32px;
  }

  .card-panel {
    height: 108px;
    font-size: 12px;
    position: relative;
    overflow: hidden;
    color: #666;
    background: #fff;
    box-shadow: 4px 4px 40px rgba(0, 0, 0, .05);
    border-color: rgba(0, 0, 0, .05);

    .card-panel-date {
      height: 12px;
      text-align: right;
      font-size: 10px;
    }

    .card-panel-body {
      height: 80px;
      line-height: 80px;
      .card-panel-description {
        float: left;
        width: 40%;
        font-size: 14px;
        text-align: center;
      }

      .card-panel-result {
        float: left;
        width: 60%;
        font-size: 24px;
      }
    }

    .card-panel-bottom {
      text-align: center;

      .card-panel-info {
        width: 100%;
        font-size: 10px;
        position: absolute;
        bottom: 0;

        .card-panel-num {
          color: #f00;
        }
      }
    }

    .card-panel-bottomDate {

      .card-panel-calendar {

      }
    }

    .card-panel-studyStyle {
        font-size: 14px;
        text-align: center;

      .card-panel-title{
        margin: 36px 0 10px 0;
      }
    }

  }
}

@media (max-width:550px) {
  .card-panel-description {
    display: none;
  }

  .card-panel-icon-wrapper {
    float: none !important;
    width: 100%;
    height: 100%;
    margin: 0 !important;

    .svg-icon {
      display: block;
      margin: 14px auto !important;
      float: none !important;
    }
  }
}
</style>
