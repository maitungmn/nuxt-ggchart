<template>
  <div>
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
  import { GChart } from 'vue-google-charts'

  export default {
    components: {
      GChart
    },
    data () {
      return {
        chartsLib: null,
        // Array will be automatically processed with visualization.arrayToDataTable function
        chartData: [
          ['X', 'Y', {'type': 'string', 'role': 'style'}],
          [1, 3, null],
          [2, 2.5, null],
          [3, 3, null],
          [4, 4, null],
          [5, 4, null],
          [6, 3, 'point { size: 18; shape-type: star; fill-color: #a52714; }'],
          [7, 2.5, null],
          [8, 3, null]
        ]
      }
    },
    computed: {
      chartOptions () {
        if (!this.chartsLib) return null
        return this.chartsLib.charts.Line.convertOptions({
          legend: 'none',
          hAxis: { minValue: 0, maxValue: 9 },
          curveType: 'function',
          pointSize: 7,
          dataOpacity: 0.3,
          height: 500,
          width: 900
        })
      }
    },
    methods: {
      onChartReady (chart, google) {
        this.chartsLib = google
      }
    }
  }
</script>
