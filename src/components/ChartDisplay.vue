<template>
  <div class="flex justify-center items-center mt-9 pr-10">
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
      chartData: {
        totalBudgetedHours: 0, // These will be populated with API data
        usedThisQuarter: 0,
        usedThisPeriod: 0,
        hoursRemaining: 0,
      },
    };
  },
  methods: {
    addChartData() {
      const data = {
        labels: ['Total Budgeted', 'Used this Quarter', 'Used this Period', 'Hours Remaining'],
        datasets: [
          {
            label: 'Hours',
            data: [
              this.chartData.totalBudgetedHours,
              this.chartData.usedThisQuarter,
              this.chartData.usedThisPeriod,
              this.chartData.hoursRemaining,
            ],
            backgroundColor: 'rgba(75, 192, 192, 0.5)',
            borderColor: 'rgba(75, 192, 192, 1)',
            borderWidth: 1,
          },
        ],
      };

      this.renderChart(data);
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
          indexAxis: 'y',
          scales: {
            x: {
              beginAtZero: true,
              max: 150,
            },
            y: {
              barThickness: 24,
            },
          },
          plugins: {
            legend: {
              position: 'bottom',
            },
          },
          maintainAspectRatio: false,
        },
      });
    },
  },
  mounted() {
    // TODO: Replace these test values with actual API call to fetch data
    this.chartData.totalBudgetedHours = 117;
    this.chartData.usedThisQuarter = 86.25;
    this.chartData.usedThisPeriod = 10.75;
    this.chartData.hoursRemaining = 30.75;

    // After setting the data, adds it to the chart
    this.addChartData();
  },
};
</script>

<style scoped>
.chart-container {
  position: relative;
  height: 30vh;
  width: 50vw;
}
</style>
