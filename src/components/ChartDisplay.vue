  <template>
    <div>
      <BarChart :chart-data="chartData" :options="chartOptions" />
    </div>
  </template>
  
  <script>
  import BarChart from '@/components/BarChart.vue';
  import AcceloService from '@/services/AcceloService';
  
  export default {
    components: {
      BarChart
    },
    data() {
      return {
        chartData: null,
        chartOptions: {
          // Customize chart options here
          scales: {
            y: {
              beginAtZero: true
            }
          }
        }
      };
    },
    async mounted() {
      try {
        // You may need to modify this part based on the actual response structure of Accelo API
        const data = await AcceloService.getData('/your-endpoint');
        this.chartData = {
          labels: data.map(item => item.label),
          datasets: [
            {
              label: 'Your Data',
              data: data.map(item => item.value),
              backgroundColor: 'rgba(75, 192, 192, 0.2)', // Customize as needed
              borderColor: 'rgba(75, 192, 192, 1)', // Customize as needed
              borderWidth: 1
            }
          ]
        };
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    }
  };
  </script>