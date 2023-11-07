<template>
    <div class="bar-chart-container">
      <canvas id="bar-chart"></canvas>
    </div>
  </template>
  
  <script>
  import { Bar, mixins } from 'vue-chartjs';
  
  export default {
    extends: Bar,
    mixins: [mixins.reactiveProp],
    props: {
      chartData: {
        type: Object,
        default: null
      },
      options: {
        type: Object,
        default: null
      }
    },
    mounted() {
      this.renderChart(this.chartData, this.options);
    }
  };
  </script>
  
  <style>
  .bar-chart-container {
    width: 100%;
    height: 400px;
  }
  </style>