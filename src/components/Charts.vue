<script setup>
const chartOptions = {
  chart: {
    id: 'vuechart-example'
  },
  xaxis: {
    categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998]
  }
}
const series = [{
  name: 'series-1',
  data: [30, 40, 35, 50, 49, 60, 70, 91]
}]

const chartOptions_pie = {
  chart: {
    width: 380,
    type: 'pie',
  },
  labels: ['Team A', 'Team B', 'Team C', 'Team D', 'Team E'],
  responsive: [{
    breakpoint: 480,
    options: {
      chart: {
        width: 200
      },
      legend: {
        position: 'bottom'
      }
    }
  }]
}
const series_pie = [44, 55, 13, 43, 22]
</script>

<template>
  <div class="gird grid-flow-col mx-10 shadow-lg rounded-lg p-10">
    <!-- <div>
      <apexchart width="500" type="bar" :options="chartOptions" :series="series"></apexchart>
    </div> -->
    <div>
      <apexchart type="pie" width="380" :options="chartOptions_pie" :series="series_pie"></apexchart>
    </div>
  </div>
</template>