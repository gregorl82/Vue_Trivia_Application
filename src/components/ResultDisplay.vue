<template lang="html">
  <div id="results-display">
    <h3>You scored {{results.correct}} out of 10!</h3>
    <p id="chart-title">Summary chart:</p>
    <chart id="results-chart" type="ColumnChart"
    :data="chartData"
    :options="chartOptions"/>
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: 'result-display',
  props: ['results'],
  components: {
    'chart': GChart
  },
  data(){
    return {
      chartData: [
        ['Answer', 'Number', {role: 'style'}],
        ['Correct', this.results.correct, 'green'],
        ['Incorrect', this.results.incorrect, 'red']
      ],
      chartOptions: {
        chart: {
          title: "Results summary"
        },
        width: 350,
        height: 500,
        vAxis: {
          title: "Number of answers",
          viewWindow: {
            min: 0,
            max: 10
          }
        },
        legend: {
          position: "none"
        }
      }
    }
  }
}
</script>

<style lang="css" scoped>

#results-chart {
  display: flex;
  padding: 8px;
  justify-content: center;
}

#results-display {
  font-size: 35px;
  font-weight: bold;
  text-align: center;
  background-color: #fff2fe;
}

#chart-title {
  font-size: 20px;
}

</style>
