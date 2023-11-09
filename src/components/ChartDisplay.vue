<template>
  <div class="flex justify-center items-center">
    <div class="chart-container">
      <canvas ref="barChart"></canvas>
    </div>
  </div>
</template>

<script>
import { Chart, registerables } from 'chart.js';
Chart.register(...registerables);

export default {
  name: 'HorizontalBarChart',
  data() {
    return {
      chart: null,
    };
  },
  methods: {
    addTestData() {
      const testData = {
        labels: ['Total Budgeted Hours', 'Used this Quarter', 'Used this Period', 'Hours Remaining'],
        datasets: [
          {
            label: 'Hours',
            data: [117, 86.25, 10.75, 30.75], // Test data. Will be replaced with data from Accelo
            backgroundColor: [
              'rgba(75, 192, 192, 0.2)',
            ],
            borderColor: [
              'rgba(75, 192, 192, 1)'
            ],
            borderWidth: 1,
          },
        ],
      };

      this.renderChart(testData);
    },
    renderChart(data) {
      const context = this.$refs.barChart.getContext('2d');
      
      if (this.chart) {
        this.chart.destroy(); // Destroy the old chart if it exists
      }

      this.chart = new Chart(context, {
        type: 'bar',
        data: data,
        options: {
          indexAxis: 'y', // Horizontal bar chart
          scales: {
            x: {
              beginAtZero: true,
              max: 150, // Set the maximum value of the x-axis
            },
            y: {
              barThickness: 24, // Control the bar thickness on the y-axis
            },
          },
          plugins: {
            legend: {
              position: 'bottom', // Display the legend at the bottom
            },
          },
          maintainAspectRatio: false, // Prevent default aspect ratio maintaining
        },
      });
    },
  },
  mounted() {
    this.addTestData(); // TODO - Replace this with Accelo API data retrieval logic later
  },
};
</script>

<style scoped>
.chart-container {
  position: relative;
  height: 40vh; /* Control the height of the chart container */
  width: 50vw; /* Adjust the width to make the chart narrower */
}
</style>
