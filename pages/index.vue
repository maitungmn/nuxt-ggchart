<template>
  <div id='app'>
    <GChart
      :settings="{packages: ['line']}"
      :data="chartData"
      :options="chartOptions"
      :createChart="(el, google) => new google.charts.Line(el)"
      @ready="onChartReady"
    />
  </div>
</template>

<script>
  import {GChart} from 'vue-google-charts'

  export default {
    components: {
      GChart
    },
    data() {
      return {
        chartsLib: null,
        // Array will be automatically processed with visualization.arrayToDataTable function
        chartData: [
          ['Day', 'A', 'B', 'C'],
          [1, 37.8, 80.8, 41.8],
          [2, 30.9, 69.5, 32.4],
          [3, 25.4, 57, 25.7],
          [4, 11.7, 18.8, 10.5],
          [5, 11.9, 17.6, 10.4],
          [6, 8.8, 13.6, 7.7],
          [7, 7.6, 12.3, 9.6],
          [8, 12.3, 29.2, 10.6],
          [9, 16.9, 42.9, 14.8],
          [10, 12.8, 30.9, 11.6],
          [11, 5.3, 7.9, 4.7],
          [12, 6.6, 8.4, 5.2],
          [13, 4.8, 6.3, 3.6],
          [14, 4.2, 6.2, 3.4]
        ],
      }
    },
    computed: {
      chartOptions () {
        if (!this.chartsLib) return null
        return this.chartsLib.charts.Line.convertOptions({
          chart: {
            title: 'Box Office Earnings in First Two Weeks of Opening',
            subtitle: 'in millions of dollars (USD)'
          },
          legend: {
            position: 'bottom'
          },

          width: 900,
          height: 500,
        })
      }
    },
    methods: {
      onChartReady(chart, google) {
        this.chartsLib = google
      }
    }
  }
</script>
